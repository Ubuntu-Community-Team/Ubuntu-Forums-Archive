---
title: "VirtualBox won't start"
date: 2007-12-16
forum: Virtualisation
---

### Post by posingaspopular on 2007-12-16
Hey all. When I try to launch something in VirtualBox, I get this error:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

So I try:

darkforce@speculum:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                                                      FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

Running dmseg:

darkforce@speculum:~$ darkforce@speculum:~$ dmseg | modprobe vboxdrv
FATAL: Module vboxdrv not found.


I'm not sure exactly what i'm missing or doing wrong, but I am very tired of trying to fix this error. any and all help is appreciated. Thanks!

-Eddie

---

### Post by x64Jimbo on 2007-12-16
have you rebooted since installing?

---

### Post by posingaspopular on 2007-12-18
I have tried to restart. Here is everything I have tried:

darkforce@speculum:~/Desktop$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb

[sudo] password for darkforce:
(Reading database ... 132072 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb) ...
dpkg: error processing virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb (--install):
trying to overwrite `/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.22-14-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
More...
Let's try to fix this:

darkforce@speculum:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darkforce@speculum:~/Desktop$ virtualbox
The program 'virtualbox' is currently not installed. You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

Let's try and ignore the issue:

darkforce@speculum:~/Desktop$ sudo dpkg --force-overwrite -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
(Reading database ... 132072 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
trying to overwrite `/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.22-14-generic
Setting up virtualbox (1.5.2-25433_Ubuntu_gutsy) ...
Installing new version of config file /etc/init.d/vboxdrv ...
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
* Starting VirtualBox kernel module vboxdrv FATAL: Module vboxdrv not found.

* Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
Starting VirtualBox host networking...done.

Hmmm let's try and check the error

darkforce@speculum:~/Desktop$ sudo cat /var/log/vbox-install.log
Makefile:68: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.. Stop.

STOP? What is this, a telegram?

sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
No candidate version found for linux-headers-2.6.17-12-generic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

Let's try another install, just for kicks:

darkforce@speculum:~/Desktop$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
(Reading database ... 132685 files and directories currently installed.)
Preparing to replace virtualbox 1.5.2-25433_Ubuntu_gutsy (using virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb) ...
* Stopping VirtualBox kernel module vboxdrv [ OK ]
Shutting down VirtualBox host networking...done.
Unpacking replacement virtualbox ...
Setting up virtualbox (1.5.2-25433_Ubuntu_gutsy) ...
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
* Starting VirtualBox kernel module vboxdrv FATAL: Module vboxdrv not found.

* Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
Starting VirtualBox host networking...done.

Let's try just...

darkforce@speculum:~/Desktop$ sudo /etc/init.d/vboxdrv setup
* Stopping VirtualBox kernel module vboxdrv [ OK ]
* Recompiling VirtualBox kernel module vboxdrv
* Look at /var/log/vbox-install.log to find out what went wrong

---

### Post by AndyCooll on 2007-12-19
Have you tried installing version of VirtualBox that is in the repositories?

:cool:

---

### Post by klenwell on 2008-07-11
I was having the same problem and came across this thread on Google.  I fixed the problem by downloading the Virtualbox 1.6 binary from the Sun site:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

or start at:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Installed without a problem.

---

