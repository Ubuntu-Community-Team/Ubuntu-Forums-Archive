---
title: "VmWare Workstation 9.0 not recognizing external tablet in USB port."
date: 2013-01-20
forum: Virtualisation
---

### Post by meteorrock on 2013-01-20
I am having a problem with my nook color not automounting in the VMware workstation 9.0.

I have Vmware tools installed and have checked the VMware options on my host Windows 7, through VM >> settings, and it shows USB controller is present. I have also checked in the removable devices options on the host for VMware, and it shows it is also enabled.

When I go to plug in my nook color however, I get a "Unable to mount nook color, error initializing camera :-60 could not lock the device" dialog box.

I also had a dialog box pop up from my Windows OS host saying it was going to give my tablet over to the "guest" OS which is ubuntu. 

~~~~~~~~~~~~~~

Looking around on google, I ran a few commands in the terminal to see if this could help someone wanting to help me with more knowledge about using virtualization and mounting a device to read and write to. Let me include some logs.

```
 meteorrock@meteorrock-virtual-machine:~$ sudo fdisk -l
[sudo] password for meteorrock: 

Disk /dev/sda: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders, total 419430400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079085

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   417333247   208665600   83  Linux
/dev/sda2       417335294   419428351     1046529    5  Extended
/dev/sda5       417335296   419428351     1046528   82  Linux swap / Solaris
meteorrock@meteorrock-virtual-machine:~$ lsusb
Bus 001 Device 005: ID 18d1:2d02 Google Inc. 
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
meteorrock@meteorrock-virtual-machine:~$ 

```

Thanks. I am stumped at this point. What did I do wrong? I am using Ubuntu 12.10 as my "guest" operating system.

---

### Post by meteorrock on 2013-01-25
Anyone? I tried to power off and power back on both of my windows 7 host and the ubuntu 12.10 guest OS and still nothing. Tried to renew my drivers for the list of USB root hubs I got listed also through the Windows 7 OS side, still no luck. They are all up and operational with working drivers.

---

### Post by meteorrock on 2013-01-25
~~~~~~~~ Working workaround~~~~~~~~~~~~ aka ugly hack.~~~~~~~ Slow transfer rate solution~~~~~~~~

Using the android debug bridge for now as a command line solution to pull and push my files to Ubuntu 12.10 and the nook color.

Make sure you have the "Developers options" enabled for Android 4.1 and up. Using cyanogenMod 10 on the nook color. Set developers options to 'on.' Android Debugging should be checked -marked. 

For more information on the android debug bridge look over this thread link here. [http://developer.android.com/tools/help/adb.html](http://developer.android.com/tools/help/adb.html)

Other solutions like the "Go-mtpfs" script for mounting android 4.0+ on up was not working on this device. 

~~~~~~~~~~~~~~~~~~~~``

Download the android default bridge with these commands.

```
sudo add-apt-repository ppa:nilarimogard/webupd8
```
```
sudo apt-get update
```
```
sudo apt-get install android-tools-adb
```

Other front end shell or GUI solutions are welcomed.

---

### Post by meteorrock on 2013-02-06
UPDATE. Permanent solution for AUTO MOUNTING Android 4.0+ devices in Ubuntu and linux. 


I found a fix for us using the nook color on linux builds. Tested it out on my machine using both Linux Mint 14.1 and Ubuntu 12.10 using CM(cyanogenmod) 10 for an auto mount solution. This is a faster transfer rate for moving files on between the nook color using CM 10 under linux. Someone back-ported a feature from Ubuntu 13.04 "Raring Ringtail." Since that linux build is still in beta, some might not be using it yet. The tool is called a "GVFS-with MTP."  This tool will AUTOMOUNT your nook color in linux. The source for this information is here. [http://www.webupd8.o...support-in.html](http://www.webupd8.o...support-in.html)

 First we will have to add the PPA (Personal Package Archive) through the terminal in these linux builds.

 1. To add the Gvfs (and libmtp) PPA created by the Gvfs MTP backend developer in Ubuntu 12.04 or 12.10, use the following commands:

```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
```
```
sudo apt-get update
```

 2. Then, launch Software Updater (previously known as Update Manager) and install the available updates.


 3. Once everything has been updated successfully, RESTART your computer, unlock your nook color, connect it via USB and it should show up in your file manager. (Tested with Nautilus 3.6+).

 If you don't unlock your Android 4.0+ device, it may show up as empty in the file manager, at least that was the case for me.

 ~~~~~~~~~~~~~~~~~~~~~```

 Connect your nook color( or other android 4.0+ device) in linux to now see the nook color icon pop up on the desktop!! You can now move and transfer files that way instead of using the android ADB through the terminal. This is a faster solution on transferring files through your nook color to Ubuntu 12.10 or other linux builds.

---

