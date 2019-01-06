FROM tensorflow/tensorflow:1.10.1-gpu 

ENV DEBIAN_FRONTEND noninteractive
ENV LANG en_US.UTF-8

RUN sed 's/main$/main universe/' -i /etc/apt/sources.list
RUN apt-get update && \
apt-get install -y --no-install-recommends --fix-missing \
build-essential autoconf automake git \
wget usbutils unzip vim \
software-properties-common libxext-dev libxrender-dev libxslt1.1 libxtst-dev libgtk2.0-0 libcanberra-gtk-module \
locales && \
locale-gen en_US.UTF-8

# ros-kinetic
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
RUN apt-key adv --keyserver ha.pool.sks-keyservers.net --recv-keys 421C365BD9FF1F717815A3895523BAEEB01FA116
RUN apt-get update && \
apt-get install -y --no-install-recommends \
ros-kinetic-desktop ros-kinetic-libuvc-camera ros-kinetic-image-view ros-kinetic-cv-bridge ros-kinetic-cv-camera && \
rm -rf /var/lib/apt/lists/*
RUN rosdep init && \
rosdep update
RUN apt-get update && \
apt-get install -y --no-install-recommends \
python-rosinstall python-rosinstall-generator python-wstool

# tensorflow deps
RUN apt-get install python-tk
RUN pip install requests
