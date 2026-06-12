---
title: "Error message when attempting to use VirtualBox"
date: 2008-10-07
forum: Virtualisation
---

### Post by lighthammer on 2008-10-07
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I went to Synaptic Package Manager did a search for VirtualBox kernal driver (vboxdrv kernel module) and there were around 15 different listings. I just grabbed the first one I saw because they all looked the same. I went to start up VirtualBox again and still nothing.

I am attempting to install WinXP from a cd. I am using Ubuntu Hardy 8.04

---

### Post by brsmits on 2008-10-07
I am getting the same thing, trying to reinstall and it doesn't help.  Though, I am a linux newbie, so maybe I am missing something simple.

---

### Post by howefield on 2008-10-07
It is telling you what to do

"Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic.."

In a terminal type uname -r  and make a note of the version the command returns, and install the corresponding modules.

I'd uninstall it to be honest, and downloadthe PUEL (Personal Use and Evaluation Licence) from virtualbox website which has a few more features including usb support. 

[http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads)

---

### Post by snova on 2008-10-07
First off, reinstalling almost never helps anything on Linux.

Secondly, there are a lot of different packages for a lot of different kernels, for several different versions. Just installing "the first one you see" has a high chance of getting the wrong one. So get rid of that for now.

Since you don't sound like somebody who'd be changing your kernel, just install "virtualbox-ose-modules-generic", which should depend on the generic one.

You're going to have other troubles, just to let you know. Search around for adding yourself to the "vboxusers" group, as that's another necessary step.

---

### Post by lighthammer on 2008-10-08
*Duplicate Message*

---

### Post by lighthammer on 2008-10-08
I downloaded VirtualBox from the website. I clicked on the Linux Host for the Ubuntu Hardy Heron (8.04) i386 version and put it in my desktop. When I clicked on the file to start the installation, it says, "Error - Wrong Architecture 'i386'"

Which is the right one to download?

*Edit* Snova, I did put myself in that Vboxuser group but I still had issues.

---

