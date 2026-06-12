---
title: "Help! Difficuties installing PX-TV402 in Dapper x64"
date: 2007-11-25
forum: Virtualisation
---

### Post by jsmithy on 2007-11-25
Hello, :)

I'm a new to Linux and Ubuntu but I see a lot of reasons to move from Winblows.

I am trying to install the driver for a Plextor PX-TV402U USB2 PVR.

I went to a site that gives the following instructions in how to do it:

# Install required development packages (this is a big download)
sudo apt-get install linux-kernel-devel linux-headers-generic fxload libncurses5-dev
# Get the driver source
wget [http://nikosapi.org/software/WIS_Go7007/wis-go7007-linux-0.9.8-patched.tar.bz2](http://nikosapi.org/software/WIS_Go7007/wis-go7007-linux-0.9.8-patched.tar.bz2)
# Unpack the source
tar -xjvf wis-go7007-linux-0.9.8-patched.tar.bz2
t# Decend into source directory
cd wis-go7007-linux-0.9.8-patched
# Compile the software
make
# Install the software
sudo make install

Because the first instruction included  linux-headers-generic, I would get an error stating not to be found.  I substituted  linux-headers-generic by linux-headers-2.6.15-29-amd64-generic

The process for the first instruction found everything and installed all.  I had already installled linux-headers-2.6.15-29-amd64-generic and it so notified.

I downloaded the driver and untar it in my home directory.  Changed to the directory that was created and executed:

make

the output was:

***** Using kernel source in /usr/src/linux-headers-2.6.15-29-amd64-generic *****

make modules -C /usr/src/linux-headers-2.6.15-29-amd64-generic M=/home/oem/wis-go7007-linux-0.9.8-patched/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
  CC [M]  /home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.o
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:30:27: error: media/tvaudio.h: No such file or directory
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:228: error: ‘TVAUDIO_INPUT_EXTERN’ undeclared here (not in a function)
/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.c:238: error: ‘TVAUDIO_INPUT_TUNER’ undeclared here (not in a function)
make[2]: *** [/home/oem/wis-go7007-linux-0.9.8-patched/kernel/go7007-usb.o] Error 1
make[1]: *** [_module_/home/oem/wis-go7007-linux-0.9.8-patched/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-29-amd64-generic'
make: *** [all] Error 2

Being new to all this, I do not know what went wrong.

Can you help me?

Peace to all :)

NOTE: To see how it was solved, look for a similar post in the Multimedia and Video section of the forums.

Note:  I'm posting this here because I will use this driver in a virtualization project with VMware, VirtualBox and any other virtualization software.

Moderators:  Please erase this post.  Since there is no help available, I will post in another area of the forum.

---

