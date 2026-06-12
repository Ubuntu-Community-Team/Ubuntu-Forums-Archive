---
title: "VirtualBox / Karmic"
date: 2009-12-16
forum: Virtualisation
---

### Post by cybernet on 2009-12-16
```
root@xList:/home/cybernet# apt-get install virtualbox-3.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsdl-ttf2.0-0
The following NEW packages will be installed:
  libsdl-ttf2.0-0 virtualbox-3.1
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 45.7MB of archives.
After this operation, 92.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ro.archive.ubuntu.com karmic/main libsdl-ttf2.0-0 2.0.9-1build1 [16.6kB]
Get:2 http://download.virtualbox.org karmic/non-free virtualbox-3.1 3.1.0-55467_Ubuntu_karmic [45.7MB]
Fetched 45.7MB in 33s (1,366kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.1.
(Reading database ... 159691 files and directories currently installed.)
Unpacking virtualbox-3.1 (from .../virtualbox-3.1_3.1.0-55467%5fUbuntu%5fkarmic_amd64.deb) ...
Selecting previously deselected package libsdl-ttf2.0-0.
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1build1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Setting up virtualbox-3.1 (3.1.0-55467_Ubuntu_karmic) ...
Adding group `vboxusers' (GID 127) ...
Done.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
 * Starting VirtualBox kernel module                                            
 * Cannot create device /dev/vboxdrv with major 10 and minor  55

Setting up libsdl-ttf2.0-0 (2.0.9-1build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
You have new mail in /var/mail/root
root@xList:/home/cybernet# 

```

so i can't create that device
before that i had this error ( see screenshot )

can you provide any help


root@xList:/home/cybernet# uname -a
Linux xList 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

---

### Post by cybernet on 2009-12-16
no one ?:o

---

### Post by EricDrijv on 2009-12-16
Sometimes Virtualbox.org doesn't work in Karmic
First do a sudo apt-get remove virtualbox-3.1
You can install the Virtualbox from Sun it always works
[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

---

### Post by cybernet on 2009-12-16
new on forums but your wise :lolflag:
thanks it worked:popcorn:

---

### Post by EricDrijv on 2009-12-16
Yes I'm new on this forum, but I'm also active on the Dutch Ubuntu forum.
If this thread is solved you should change the prefix to [SOLVED], so others can see the status of the thread:guitar:

---

### Post by manolomanolo on 2010-01-09
> Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. [SIZE="4"]**Users of Ubuntu,**[/SIZE] Fedora or Mandriva **[SIZE="4"]should install the DKMS package first[/SIZE]**. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

As the error message says, you must install DKMS package first and then executing 'vboxdrv setup'.

So, please try and run

```
sudo apt-get install dkms
```
and then
```
sudo /etc/init.d/vboxdrv setup
```

it worked for me :guitar:

---

### Post by mkvnmtr on 2010-01-10
There is a manual on the Sun site that you can download. When I changed from the OSE in the repositories to the Sun version I found the manual. It has been very helpful with things like installing the dkms package and other quirks of getting things to work.

---

