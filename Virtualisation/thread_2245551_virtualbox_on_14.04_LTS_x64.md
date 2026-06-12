---
title: "virtualbox on 14.04 LTS x64"
date: 2014-09-24
forum: Virtualisation
---

### Post by johnsail on 2014-09-24
I have tried to upgrade to virtualbox 4.3.16 and failed (although software manager seems to think that it is installed)
I cannot run from the sofware manger icon on the launch bar as the icon options do not display in a readable form and when the icon is selected the screen goes mad and nothing is readable;
typing "virtualbox" at the terminal produces the following:-
----------------------------------------------
```
john@tadw004:~$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (3.2.0-24-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "S&tart" under id 16 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Pause" under id 17 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "&Reset" under id 18 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "D&iscard saved state..." under id 24 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Re&fresh..." under id 25 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Show in File Manager" under id 27 
Qt WARNING: void DBusMenuExporterPrivate::addAction(QAction*, int): Already tracking action "Create Shortcut on Desktop" under id 28 
------------------------------------------------
The Oracle VM VirtualBox Manager screen is displayed and shows my vrtual machines.

Selecting a virtualisation rresults in the following errors:-
-------------------------------------------------
Failed to open a session for the virtual machine Win32_tadw004.

The virtual machine 'Win32_tadw004' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}

```----------------------------------------------
Followed by:-

 ```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```
---------------------------------------------

Executing the suggested [COLOR=#0000ff]/etc/init.d/vboxdrv setup [/COLOR]procedure produces dkms errors suggesting that I am trying to install a 4.3.16 entry that is already there.

Following suggestions from various forums etc my system seems to need linux-headers-3.2.0-24-generic which I do not seem to have on my sysytem and cannot find them anywhere on the web.

I have various other flavours in /usr/src but not 3.2.0-24-generic.

Any help will be geatefully reveived as I have been struggling with this for days.

---

### Post by slickymaster on 2014-09-24
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by whitesmith on 2014-09-24
Please try running these commands sequentially:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get check
```

And now try running the application again. "Kernel driver not installed" indicates missing/broken packages these incantations should fix (maybe).

---

### Post by johnsail on 2014-09-24
Hi Whitesmith
Thanks for the reply.
Unfortunately I still get the same errors,

---

### Post by whitesmith on 2014-09-24
Perhaps someone with greater knowledge of VirtualBox can be of further help. At least you now have a clean system (I'm a glass-half-full-guy)! Best of luck!

---

### Post by slickymaster on 2014-09-24
Hi johnsail, can you please the following:
First install the kernel headers and build tools by running in a terminal window these commands, one at a time:```
sudo apt-get install build-essential module-assistant
sudo m-a prepare
```After that compile, virtualbox kernel driver with the commanded as reported by the error message you got```
sudo /etc/init.d/vboxdrv setup
```If all goes well you'll be presented with an output similar to```
Stopping VirtualBox kernel modules ...done.
Recompiling VirtualBox kernel modules ...done.
Starting VirtualBox kernel modules ...done.
```

---

### Post by johnsail on 2014-09-25
hi.
followed your suggestion and this is the output:-

john@tadw004:~$ sudo apt-get install build-essential module-assistant
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
module-assistant is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 11 not to upgrade.
john@tadw004:~$ sudo m-a prepare
Getting source for kernel version: 3.2.0-24-generic
apt-get install linux-headers-3.2.0-24-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-24-generic
E: Couldn't find any package by regex 'linux-headers-3.2.0-24-generic'
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 11 not to upgrade.

Done!
john@tadw004:~$ sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modulesError! Could not locate dkms.conf file.
File:  does not exist.
 ...done.
Trying to register the VirtualBox kernel modules using DKMSError! DKMS tree already contains: vboxhost-4.3.16
You cannot add the same module/version combo more than once.
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)
john@tadw004:~$ 

and this is the content of vbox-install.log :-

Uninstalling modules from DKMS
Attempting to install using DKMS
Failed to install using DKMS, attempting to install without
Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

John

---

### Post by slickymaster on 2014-09-25
No I am confused, you say that you're running Ubuntu 14.04 which includes the 3.13.0-32.57 Ubuntu Linux kernel which is based on the v3.13.11 upstream stable Linux kernel, but your system is coming up with 3.2.0-24-generic. I wonder if you are somehow booting into an old kernel, even though you have newer ones.

Can you please post the output you get of```
lsb_release -a && uname -r
```and```
ls -l /boot
```

---

### Post by johnsail on 2014-09-25
Hi
output from 
lsb_release -a && uname -r

```
john@tadw004:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
3.2.0-24-generic
john@tadw004:~$ 

```
output from 
ls -l /boot

```
john@tadw004:~$ ls -l /boot
total 120960
-rw-r--r-- 1 root root   524784 Oct 20  2009 abi-2.6.28-16-generic
-rw-r--r-- 1 root root   624388 Mar 24  2010 abi-2.6.31-21-generic
-rw-r--r-- 1 root root   646299 Apr  8  2011 abi-2.6.32-31-generic
-rw-r--r-- 1 root root   730744 Sep 28  2011 abi-2.6.38-12-generic
-rw-r--r-- 1 root root   730503 Oct  7  2011 abi-3.0.0-12-generic
-rw-r--r-- 1 root root   791075 May 21  2012 abi-3.2.0-24-generic
-rw-r--r-- 1 root root    90655 Oct 20  2009 config-2.6.28-16-generic
-rw-r--r-- 1 root root   105746 Mar 24  2010 config-2.6.31-21-generic
-rw-r--r-- 1 root root   110567 Apr  8  2011 config-2.6.32-31-generic
-rw-r--r-- 1 root root   130326 Sep 28  2011 config-2.6.38-12-generic
-rw-r--r-- 1 root root   134754 Oct  7  2011 config-3.0.0-12-generic
-rw-r--r-- 1 root root   140341 May 21  2012 config-3.2.0-24-generic
drwxr-xr-x 2 root root     4096 Jun  1  2012 grub
-rw-r--r-- 1 root root  7079091 Nov  9  2009 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root  7570101 May  8  2010 initrd.img-2.6.31-21-generic
-rw-r--r-- 1 root root  9879184 May 25  2011 initrd.img-2.6.32-31-generic
-rw-r--r-- 1 root root 13318209 Nov 17  2011 initrd.img-2.6.38-12-generic
-rw-r--r-- 1 root root 19972413 May  6  2012 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root 20341411 Sep 12 11:01 initrd.img-3.2.0-24-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  1864822 Oct 20  2009 System.map-2.6.28-16-generic
-rw-r--r-- 1 root root  2135104 Mar 24  2010 System.map-2.6.31-21-generic
-rw-r--r-- 1 root root  2158030 Apr  8  2011 System.map-2.6.32-31-generic
-rw------- 1 root root  2656729 Sep 28  2011 System.map-2.6.38-12-generic
-rw------- 1 root root  2694177 Oct  7  2011 System.map-3.0.0-12-generic
-rw------- 1 root root  2884673 May 21  2012 System.map-3.2.0-24-generic
-rw-r--r-- 1 root root     1170 Oct 20  2009 vmcoreinfo-2.6.28-16-generic
-rw-r--r-- 1 root root     1336 Mar 24  2010 vmcoreinfo-2.6.31-21-generic
-rw-r--r-- 1 root root     1336 Apr  8  2011 vmcoreinfo-2.6.32-31-generic
-rw------- 1 root root     1369 Sep 28  2011 vmcoreinfo-2.6.38-12-generic
-rw------- 1 root root     1367 Oct  7  2011 vmcoreinfo-3.0.0-12-generic
-rw-r--r-- 1 root root  3513536 Oct 20  2009 vmlinuz-2.6.28-16-generic
-rw-r--r-- 1 root root  3949024 Mar 24  2010 vmlinuz-2.6.31-21-generic
-rw-r--r-- 1 root root  4055840 Apr  8  2011 vmlinuz-2.6.32-31-generic
-rw------- 1 root root  4527136 Sep 28  2011 vmlinuz-2.6.38-12-generic
-rw------- 1 root root  4658096 Oct  7  2011 vmlinuz-3.0.0-12-generic
-rw------- 1 root root  4965968 May 21  2012 vmlinuz-3.2.0-24-generic
john@tadw004:~$
```

---

### Post by slickymaster on 2014-09-25
I would advise you to upgrade your kernel.

If you want to do it, **be aware that proprietary drivers may or may not work correctly with this kernel version. You need to rebuilt (or install) your video driver after kernel update**.

In a terminal window run the following commands, one by one:```
cd /tmp/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb
sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb
```
Reboot and and try again```
sudo m-a prepare
sudo /etc/init.d/vboxdrv setup
```

---

### Post by johnsail on 2014-09-26
Slickymaster, Thank you so much for following my problem through.<br>Prior to following your latest sugetions I had reason to reboot and on power up got the error:<br><br>System program problem detrected<br>Do you want to reprt the prpblem now.<br>I responded to reprt the problem but nothing seemed to happen and the sytem continued to boot.<br><br>Once the screen had refreshed I got the messsage:-<br>The Application Oracle VM Virtualbox has closed unexpectedly<br>Do you want to send error report?<br>I replied positive and was then asked:-<br>Do you want to re-launch or remain closed?<br>Seemed sensible to answer "remain closed".<br><br>I then followed your instructions, step by step, and all seemed to work ok with the exception of a dkms error saying that it had failed due to trying to add a dkms tree entry that was already there&nbsp; 4.3.16,<br>It then proceeded to run without dkms and completed successfully.<br><br>I was the able to run successfully the vboxdrv setup&nbsp; instructions.<br><br>Following the required reboot I found that my vrtualbox did run correctly and not only that the program problem on reboot had disappeared as had my problems with the launcher icons<br> not displaying properly and the search computer program not displaying anything readable at all. This I have been running in the gnral help forum and I shall now close it rthanks to your help.<br><br>I cannot thank you enough.<br><br>Johnsail<br>Johnsail

---

### Post by slickymaster on 2014-09-26
You're welcome. I'm just glad you got fixed and running.

Now, can you just do me a favor and mark the thread SOLVED so other people searching the forums know that it provides a working solution for their problem. Just follow the link in my signature if you don't know how to do it.

Happy *buntuing. ;)

---

### Post by johnsail on 2014-09-27
Hi. Don't know if you will see this but the only thing that I have not done from your instruction is:-

**be aware that proprietary drivers may or may not work correctly with  this kernel version. You need to rebuilt (or install) your video driver  after kernel update**.

Things appeared to be OK but my screen and/or mouse have been behaving erratically and extremly slow in responding.

I do not know if a video driver was installed on my system (I did not do the original install). I need to know (1) how to find out if a video driver was installed and (2) if it was - how to rebuild it.

I am following through an ubuntu tutorial in the hope that all will become apparent but progress is slow.

Hopefully you will see this and help further.

---

### Post by slickymaster on 2014-09-29
Hey johnsail, I advise you to start a new thread (you can link it to this one as a reference) for this new issue you're facing. From [here]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811"):> **Post only one thread on your topic**. Posting multiple threads dilutes community effort, and makes it more difficult for others to help.
> **johnsail said:**
> <...snip...>
I do not know if a video driver was installed on my system (I did not do the original install). I need to know (1) how to find out if a video driver was installed and (2) if it was - how to rebuild it.<...snip...>
To see the video driver used run```
lshw -c video | grep 'configuration'
```or for more detail```
lshw -c video
```

---

### Post by johnsail on 2014-10-01
Below is the output from the two steps you suggest.

john@tadw004:~$ sudo lshw -c video | grep 'configuration'
[sudo] password for john: 
       configuration: driver=radeon latency=0
john@tadw004:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: RV610 [Radeon HD 2400 PRO]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff
john@tadw004:~$ 

Not sure what to do next but I will try to open a new thread with a link to this

---

### Post by suresh23 on 2015-09-22
Hope this will help

1) To install the dependancy 

suresh@suresh-dell:~$ sudo apt-get install dkms bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential

2) Adding repository

suresh@suresh-dell:~$ sudo sh -c "echo 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) '$(lsb_release -cs)' contrib non-free' > /etc/apt/sources.list.d/virtualbox.list"

3) Oracle public key downloading

suresh@suresh-dell:~$ wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

4) Repository update

suresh@suresh-dell:~$ sudo apt-get update

5)VirtualBox installation

suresh@suresh-dell:~$ sudo apt-get install virtualbox-4.3

6) Rebuilding kernel modules

suresh@suresh-dell:~$ sudo /etc/init.d/vboxdrv setup

7) Start the VirtualBox

suresh@suresh-dell:~$ VirtualBox

---

### Post by slickymaster on 2015-09-22
Closed thread.

This thread is almost one year old and the OP's issue related to Virtual Box 4.3.16, which is by now long dead.

---

