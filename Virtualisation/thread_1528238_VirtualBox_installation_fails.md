---
title: "VirtualBox installation fails"
date: 2010-07-10
forum: Virtualisation
---

### Post by human118 on 2010-07-10
First I added the Vbox to the Repo and added the key:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

Then:
```
sudo apt-get install virtualbox-3.2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-3.2
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 49.4MB of archives.
After this operation, 96.7MB of additional disk space will be used.
Get:1 http://download.virtualbox.org/virtualbox/debian/ lucid/non-free virtualbox-3.2 3.2.6-63112~Ubuntu~lucid [49.4MB]
Fetched 49.4MB in 27s (1,821kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.2.
(Reading database ... 220245 files and directories currently installed.)
Unpacking virtualbox-3.2 (from .../virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-3.2 (3.2.6-63112~Ubuntu~lucid) ...
Adding group `vboxusers' (GID 125) ...
Done.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
 * Starting VirtualBox kernel module                                            
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why

Processing triggers for python-central ...

```I checked the log:
```
** Compiling vboxdrv
Makefile:170: 
*** Error: /usr/src/linux (version 2.6.32.15+drm33.5) does not match the current kernel (version 2.6.32-23-generic).  
Stop.
```When I run VirtualBox at the command line:
```
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.32-23-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
WARNING: The compilation of the vboxdrv.ko kernel module failed during the
         installation for some reason. Starting a VM will not be possible.
         Please consult the User Manual for build instructions.

```So I run sudo /etc/init.d/vboxdrv setup:
```
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```I also went through all this with the virtualbox ose install in the repo right after installing 10.4.

I would appreciate any help. I am a noob and just don't know where to go from here.

---

### Post by human118 on 2010-07-10
Nevermind, I got it. Re-installed KVMS and ran 
```
sudo /etc/init.d/vboxdrv setup
```to re-compile and all is well.

---

