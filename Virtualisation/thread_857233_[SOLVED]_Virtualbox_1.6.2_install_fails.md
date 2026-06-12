---
title: "[SOLVED] Virtualbox 1.6.2 install fails"
date: 2008-07-12
forum: Virtualisation
---

### Post by 1205919 on 2008-07-12
I am quite new to Ubuntu. I have to run Windows Xp in a virtual environment on ubuntu as some of my programs that I use on a day to day basis for my work doesn run directly under ubuntu. Not even under Wine.

Im running Ubuntu 8.04.
I have read many posts on similar isues, but cant find a solution to this particular problem.111

I had the version of Virtualbox (I think it was v5... from the Add/Remove option) installed, however I didnt see an option to connect to an external usb attached hdd which I have to be able to do. So I uninstalled and I have installed Virtualbox 1.6.2 using: "virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb", which I downloaded from the Virtualbox website.

The install runs to a point when I get the following message: "Compilation of the Kernel Module Failed. VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root." --- See attached screenshot.
The install completes but when I run Virtualbox and try to run my windows xp virtual image the following message is displayed: "Failed to start the virtual machine windows. 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}"

See attachment 2


I did run the comand in the help file: "/etc/init.d/vboxdrv setup", which gives me the following output: 

"paul@paul-desktop:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module                                            open: Permission denied
 *  done.
open: Permission denied
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 311: cannot create /var/log/vbox-install.log: Permission denied

open: Permission denied
 * Look at /var/log/vbox-install.log to find out what went wrong
paul@paul-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for paul: "


Pleas help as I have to have the virtual windows running by monday morning.

Thanx

Paul Kruger

---

### Post by dark_phantom on 2008-07-12
So did you get any errors when you ran it with sudo?  Try running, sudo modprobe then sudo /etc/init.d/vboxdrv setup.

---

### Post by HotShotDJ on 2008-07-12
Please install build-essential and then try again.

---

### Post by 1205919 on 2008-07-13
> **HotShotDJ said:**
> Please install build-essential and then try again.
Hi thx for the reply, would I get this in synaptics?

---

### Post by 1205919 on 2008-07-13
> **dark_phantom said:**
> So did you get any errors when you ran it with sudo?  Try running, sudo modprobe then sudo /etc/init.d/vboxdrv setup.
Hey Thx for the help.

Thisd is the respose I get:

paul@paul-desktop:~$ sudo modprobe
[sudo] password for paul: 
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
paul@paul-desktop:~$ 
paul@paul-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
paul@paul-desktop:~$ 

******

the content of vbox-install.log:

Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-386 cannot be found at
/lib/modules/2.6.24-19-386/build or /lib/modules/2.6.24-19-386/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:130: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:138: *** Error: /usr/src/linux (version 2.6.25.10-ultimate) does not match the current kernel (version 2.6.24-19-386).  Stop.

---

### Post by yuqin513 on 2008-07-13
[www.Jordan9.com](www.Jordan9.com) discount cheap nike jordan gucci prada shoes lacoste puma trainers at china factory 
Welcome to visit [www.jordan9.com,We](www.jordan9.com,We) are a professional shoes and sneaker Industrialcompany, and as af([www.jordan9.com](www.jordan9.com)) amous nike shoes factory & Stores and wholesale company.([www.google.com](www.google.com)) air force one

---

### Post by HotShotDJ on 2008-07-13
> **1205919 said:**
> Hi thx for the reply, would I get this in synaptics?Yes

---

### Post by 1205919 on 2008-07-13
> **HotShotDJ said:**
> Yes
Sorry, I dont want to sound daft but do I search for build-essential? cause I  dont get anything like that

---

### Post by HotShotDJ on 2008-07-13
> **1205919 said:**
> Sorry, I dont want to sound daft but do I search for build-essential? cause I  dont get anything like thatDouble-check your typing ... it is there.

---

### Post by 1205919 on 2008-07-13
I have checked its not there, I even updated my software sources, it still doesnt show

**********

ok I figured out that i can use this:
sudo apt-get install build-essential     in terminal, its installing now....

---

### Post by 1205919 on 2008-07-13
OK I installed build-essential - makes no difference, still get this when I try and start my virtual winxp:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

---

### Post by HotShotDJ on 2008-07-13
> **1205919 said:**
> Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.What happens when you run the command suggested in the error message.  In Ubuntu, to run a command as root, preface it with "sudo" like this:```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by 1205919 on 2008-07-13
This is what I get:

[COLOR="Red"]paul@paul-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for paul: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
paul@paul-desktop:~$ 
paul@paul-desktop:~$ [/COLOR]




****


and the content of /var/log/vbox-install.log :

*
[COLOR="#ff0000"]Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-386 cannot be found at
/lib/modules/2.6.24-19-386/build or /lib/modules/2.6.24-19-386/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:130: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:138: *** Error: /usr/src/linux (version 2.6.25.10-ultimate) does not match the current kernel (version 2.6.24-19-386).  Stop.[/COLOR]


*******


I really dont have the faintest idea what all of the above means, so any help would be much appreciated...

---

### Post by HotShotDJ on 2008-07-13
> **1205919 said:**
> I really dont have the faintest idea what all of the above means, so any help would be much appreciated...At this point, I think you should do a complete removal of VirtualBox from the command line:```
sudo apt-get remove virtualbox --purge
```And then reinstall it (double click on the deb file you downloaded from Sun).

---

### Post by 1205919 on 2008-07-13
Youre the best, Thx its working

But how do i get the virtual windows to recognise my external hdd on usb

---

### Post by 1205919 on 2008-07-13
Hi All

I just want to thank all who helped me, I finaly have it all sorted out and are able to access my external hdd

You guys are all very profesional, thx again:guitar:

---

