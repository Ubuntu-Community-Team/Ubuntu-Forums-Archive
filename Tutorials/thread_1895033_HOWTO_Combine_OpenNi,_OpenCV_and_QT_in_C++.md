---
title: "HOWTO: Combine OpenNi, OpenCV and QT in C++"
date: 2011-12-13
forum: Tutorials
---

### Post by Weg7DeY8zT on 2011-12-13
Hello all. I am new to this forum and would like to start my membership with a tutorial. I had hard times making the Kinect running my my computer and I would like to share this.

I am running a 32 bit Version. It did not work on 64 bit, so I am not a big help there.

So let's start.

[SIZE=3]1) Install OpenNi, Nite and the SensorKinect driver[/SIZE]
Source: [http://www.greenfoot.org/doc/kinect/ubuntu.html](http://www.greenfoot.org/doc/kinect/ubuntu.html)

save the code below as **installKinect.sh** and run:
```

sudo sh  installKinect.sh

``````

#!/bin/sh

# Install required packages: 
apt-get install g++ libglut3-dev libboost-all-dev
apt-get install libwxbase2.8-dev libwxgtk2.8-dev wx-common

# prepare direcotry
mkdir ~/kinect
cd ~/kinect

# get openni
mkdir OpenNI
cd OpenNI
wget http://www.greenfoot.org/doc/kinect/OpenNI-Linux32.tar.bz2
tar -jxf OpenNI-Linux32.tar.bz2
sudo ./install.sh
cd ..

# install NITE
mkdir NITE
cd NITE
wget http://www.greenfoot.org/doc/kinect/NITE-Linux32.tar.bz2
tar -jxf NITE-Linux32.tar.bz2
echo '0KOIk2JeIBYClPWVnMoRKn5cdY4=' | sudo ./install.sh
cd ..

# install kinect driver
mkdir Kinect
cd Kinect
wget http://www.greenfoot.org/doc/kinect/SensorKinect-Linux32.tar.bz2
tar -jxf SensorKinect-Linux32.tar.bz2
sudo ./install.sh
cd ..


# test the installation
cd OpenNI/Samples/Bin/Release/
./Sample-NiUserTracker
cd ../../../../

```[SIZE=3]2) Install OpenCV[/SIZE]
Option 1) download and compile it, Source: [http://ozbots.org/opencv-installation/](http://ozbots.org/opencv-installation/)
Option 2) Install harpis 
```

sudo apt-get install harpia

```[SIZE=3]3) Install QT[/SIZE]
I'd recommend installing it by doing
```

sudo apt-get install qtcreator

```[SIZE=3]4) Combine it[/SIZE] :popcorn:

move the ~/kinect folder anywhere you like. In my case: /opt/kinect
then:
```

export KINECT_DIR=/opt/kinect

```make sure this is performed every time you log on


Download the sample wrapper files from:
[http://svn.comiendolimones.com/OpencvKinect]("http://www.google.com/url?sa=D&q=http://svn.comiendolimones.com/OpencvKinect&usg=AFQjCNFSbP2_tOEtKvSC_jUr_4o_RTxuig") 
Source: [http://groups.google.com/group/openni-dev/browse_thread/thread/4199705c0f408642](http://groups.google.com/group/openni-dev/browse_thread/thread/4199705c0f408642)

Place the files anywhere you like.
Now here the tricky part. Linking OpenCV and OpenNi with QT. This is done by this handy makefile.
```

OSTYPE := $(shell uname -s)

BIN_DIR = .

INC_DIRS =  /usr/include/ni

SRC_FILES = *.cpp

EXE_NAME = SimpleViewer

ifeq ("$(OSTYPE)","Darwin")
    LDFLAGS += -framework OpenGL -framework GLUT
else
    USED_LIBS += glut cxcore cv highgui cvaux ml QtGui QtCore pthread
endif

USED_LIBS += OpenNI


CFLAGS        = -pipe -O2 -I/usr/local/include/opencv  -D_REENTRANT $(DEFINES)
CXXFLAGS      = -pipe -O2 -I/usr/local/include/opencv  -D_REENTRANT $(DEFINES)

include  $(KINECT_DIR)/OpenNI/Samples/Build/Common/CommonCppMakefile

```make sure opencv is installed in the paths I specified, otherwise you will have to change them.
Create a file called Makefile in the folder where you placed the files. The folder should then look like this:

[LIST]
[*][CVKinectWrapper.cpp]("http://svn.comiendolimones.com/OpencvKinect/CVKinectWrapper.cpp")
[*][CVKinectWrapper.h]("http://svn.comiendolimones.com/OpencvKinect/CVKinectWrapper.h")
[*][NiSimpleViewer.cpp]("http://svn.comiendolimones.com/OpencvKinect/NiSimpleViewer.cpp")
[*]Makefile
[/LIST]
Now run
```

make

```and it should work!




Hope this is of some help.

---

