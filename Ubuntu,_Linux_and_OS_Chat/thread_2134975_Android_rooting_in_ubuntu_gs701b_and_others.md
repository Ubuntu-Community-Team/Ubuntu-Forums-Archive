---
title: "Android rooting in ubuntu gs701b and others"
date: 2013-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by vanquishedangel on 2013-04-12
ok I got it rooted and here is is how to the best of my memory. (windows users will need to install drivers from pdanet and have an adb shell or android-sdk) This is actually for a **gs701b** but may work for others. Especially the a10 or a13 series

**1)** On Ubuntu you need to get eclipse and android-tools-adb from the software center or synaptic also put your tablet in usb debugging mode(settings-->developer options in your android device)

Sudo apt-get install eclipse android-tools-adb

**2)** Once those are downloaded and installed you will need to edit a few files, so open a terminal and run:

lsusb

mine looks like this:

Bus 003 Device 002: ID 0e8f:0002 GreenAsia Inc. 
Bus 004 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 006: ID 10d6:0c02 Actions Semiconductor Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

In this list you will need to find your device and my tablet is:

Bus 001 Device 006: ID **10d6:0c02** Actions Semiconductor Co., Ltd

**3)** now you need to edit the file located in .android this will be in you home folder and you need to view hidden files to see it. the command would be:

sudo leafpad /home/(username)/.android/adb_usb.ini (or) sudo gedit /home/(username)/.android/adb_usb.ini

**4)** Add the vendor id and device id to this list (mine are bolder above) and delete anything other than numbers in this file mine looks like this:

0x10d6
0x2080
0x18d1
0x0c02

**5)** Then you will need to edit a udev file and create a rule, the command is:

sudo leafpad /etc/udev/rules.d/99-android.rules (or) sudo gedit /etc/udev/rules.d/99-android.rules

**6)** And add these lines to the bottom:

#Actions Semiconductor
SUBSYSTEM=="usb", SYSFS{idVendor}=="**0x0c02**", MODE="0666"
#Actions Semiconductor
SUBSYSTEM=="usb", ATTRS{idVendor}=="**10d6:0c02**", SYMLINK+="android_adb", MODE="0666" GROUP="plugdev"
TEST=="/var/run/ConsoleKit/database", \
RUN+="udev-acl --action=$env{action} --device=$env{DEVNAME}"

**7)** The bold part will be what you got for lsusb in the terminal earlier. These steps will make the tablet visible to ubuntu. Ubuntu does not need drivers for tablets in most cases and that is true for this one. at this point open a terminal and type this:

adb devices

And you should see your tablet in the list, mine looks like this:

* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
Actions Semi. 71197615	device

**8)** Now from here the process should be a breeze, easy peasy. You will need to download this file: (windows people start here.)

[http://higgs.rghost.ru/download/42793533/35f64c45408c3caafb33caf1e44da5191b108867/root_gs701b_.rar](http://higgs.rghost.ru/download/42793533/35f64c45408c3caafb33caf1e44da5191b108867/root_gs701b_.rar)

**9)** Assuming it downloads to your download folder extract the file there, then open a terminal and go to the folder:

cd /home/(username)/Downloads/gs701b-root/files

**10)** Now we install superuser to the device and push some software:

1. adb Install Superuser.apk
2. adb push busybox /sdcard/
3. adb push su /sdcard/

**11)** In the same terminal now we open adb:

adb shell

**12)** enter the command for superuser

su

**13)** Then you will get a password prompt, this password is "actions123" without the "

**14)** Now these you will copy and paste in order each one:

1. mount -o remount,rw /system
2. mv /system/xbin/su /system/xbin/oldsu
3. cp /sdcard/busybox /system/bin/busybox
4. cp /sdcard/su /system/bin/su
5. chmod 06755 /system/bin/su
6. chmod 0755 /system/bin/busybox
7. ln -s /system/bin/su /system/xbin/su
8. exit su (may say something about a bad number)
9. exit
10. adb reboot

---

### Post by BStrizzy on 2013-04-18
nice set of instructions!

---

