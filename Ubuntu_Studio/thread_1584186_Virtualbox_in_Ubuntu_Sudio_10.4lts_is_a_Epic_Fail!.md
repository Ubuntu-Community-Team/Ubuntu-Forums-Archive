---
title: "Virtualbox in Ubuntu Sudio 10.4lts is a Epic Fail!"
date: 2010-09-28
forum: Ubuntu Studio
---

### Post by Dr Zin on 2010-09-28
I would say is...![-(  If you going to a distro that has to work of I/O's that can not work inside of a VM at lest make it work with VM's inside of the distro. When it come to Ubuntu Studio period.  

  I think that is the only issue I have VM'ing is the whole I/O issue. I know that is are issues with have a Type 2 (or hosted) hypervisor or paravirtualization. I think that is important that this issue is worked on. I would have posted this on the VirtualBox forum but you see its Ubuntu Studio kernel. =;

:-k> Your kernel headers for kernel 2.6.32-21-preempt cannot be found at
/lib/modules/2.6.32-21-preempt/build or /lib/modules/2.6.32-21-preempt/source.](*,)
  
  Unless if you don't have the hardware to work off of, yeah I can see just Ubuntu install would work. I have been around the block once. LOL  So my rant is out the way, well .... not completely. SO..... Does any know how to mod this with care! I am as well looking at submitting this as a bug and a script or two.

```
sudo apt-get install virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-3.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/49.7MB of archives.
After this operation, 97.7MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.2.
(Reading database ... 180490 files and directories currently installed.)
Unpacking virtualbox-3.2 (from .../virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-3.2 (3.2.8-64453~Ubuntu~lucid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
 * Starting VirtualBox kernel module                                                          
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why

Processing triggers for python-central ...

```




```
sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                                           *  done.
 * Recompiling VirtualBox kernel module                                                       
 * Look at /var/log/vbox-install.log to find out what went wrong

```

```
sudo gedit /ver/log/vbox-install.log

```

:-k

```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.2.8

------------------------------
Deleting module version: 3.2.8
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.2.8/source ->
                 /usr/src/vboxdrv-3.2.8

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.32-21-preempt cannot be found at
/lib/modules/2.6.32-21-preempt/build or /lib/modules/2.6.32-21-preempt/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-21-preempt package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

---

### Post by AutoStatic on 2010-09-29
Install the package **linux-headers-preempt** and try again.

---

### Post by sheehanje on 2010-09-29
I wish the EPIC FAIL tag would go away.

I've been running Virtual Box on Ubuntu Studio since 9.04, and 10.04 is no different.  If you expect world class virtualization performance, don't put it on studio.  If you are using studio for what it is designed to do, then you will be using way too many resources to run a bunch of virtual machines.  If you, like myself, just need it for testing or running a single virtual machine and don't expect full bare metal performance, then it works as advertised.

Do as autostatic says, and install the headers for your kernel.  The module should build fine then.  And remember, if you happen to do any updates that update the kernel, the module needs to get rebuilt, but it should automatically build it when you launch VB after the first install.

---

### Post by Dr Zin on 2010-09-30
:biggrin: LOL! same about the the "Epic Fail!" go as well. I did it out humor.

I will a reinstall of the Kernel after the apt-get update before or after install VB?

---

### Post by AutoStatic on 2010-10-01
Before installing VB.

---

