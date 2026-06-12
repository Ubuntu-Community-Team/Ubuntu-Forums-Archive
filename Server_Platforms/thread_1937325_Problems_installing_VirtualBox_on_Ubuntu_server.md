---
title: "Problems installing VirtualBox on Ubuntu server"
date: 2012-03-07
forum: Server Platforms
---

### Post by BobGbob on 2012-03-07
I am trying to install VirtualBox on an Ubuntu 11.10 server.  First of all,  am i already barking up the wrong tree?   :)

I have run trough the install process, but am getting error when I type in "VirtualBox"   As you can see below,  I tried to uninstall it as well but am still getting the 'unmet dependencies"  error.   Any ideas,  suggestions, etc.   


here is what is happening:  
tardis@faceofbo:~$ sudo VirtualBox


WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (3.0.0-16-generic-pae) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libGL.so.1: cannot open shared object file: No such file or directory

tardis@faceofbo:~$ sudo /etc/init/d/vboxdrv setup

sudo: /etc/init/d/vboxdrv: command not found

tardis@faceofbo:~$ apt-get remove virtualbox-4.1
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

tardis@faceofbo:~$ sudo apt-get remove virtualbox-4.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:

The following packages have unmet dependencies:
 alsa-utils : Depends: libsamplerate0 but it is not going to be installed
 libasound2-plugins : Depends: libsamplerate0 but it is not going to be installed
 pulseaudio : Depends: libsamplerate0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

tardis@faceofbo:~$ sudo apt-get remove virtualbox-4.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 alsa-utils : Depends: libsamplerate0 but it is not going to be installed
 libasound2-plugins : Depends: libsamplerate0 but it is not going to be installed
 pulseaudio : Depends: libsamplerate0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

tardis@faceofbo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsamplerate0
The following NEW packages will be installed:
  libsamplerate0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
239 not fully installed or removed.
Need to get 0 B/1,340 kB of archives.
After this operation, 1,552 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 112372 files and directories currently installed.)
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.7-3ubuntu1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libsamplerate0_0.1.7-3ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/libsamplerate0_0.1.7-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

tardis@faceofbo:~$

---

### Post by snowpine on 2012-03-07
A simple typo. You were supposed to:

> **BobGbob said:**
> sudo /etc/init.d/vboxdrv setup


But you typed:

> **BobGbob said:**
> sudo /etc/init/d/vboxdrv setup


Happens to the best of us. :)

ps It is not usually necessary to run VirtualBox with "sudo."

---

### Post by BobGbob on 2012-03-08
Thanks Snowpine.   

I am pretty much a newbie at Linux.  But I love this stuff!!  :)

I have been trying to set up VirtualBox on an Ubuntu 11.10 server.   I found info now regarding setting up VirtualBox on a headless server.     May or may not work, but I am having fun figuring it all out.  

Bob

---

### Post by Cheesemill on 2012-03-08
Have you seen this:

[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-11.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.1-on-a-headless-ubuntu-11.10-server)

---

