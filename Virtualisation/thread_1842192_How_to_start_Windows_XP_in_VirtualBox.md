---
title: "How to start Windows XP in VirtualBox?"
date: 2011-09-10
forum: Virtualisation
---

### Post by paker on 2011-09-10
Installed VirtualBox from Synaptic Package Manager. That's as far as I can go. I put the XP cd in CD ROM and started VM. Error message:

Fatal! No bootable medium found.

I changed boot sequence from HD > CD-ROM to CD-ROM > HD. Same error. What am I missing?

10.04 LTS 64 bit

---

### Post by lykwydchykyn on 2011-09-10
Sounds like your guest's CD drive is not set to the host drive; what version of virtualbox are you using?  The interface for selecting the CD drive has changed over the last few versions.

---

### Post by wildmanne39 on 2011-09-10
Hi, in virtualbox click on settings, then storage and your settings for storage should look basically like the screenshot.

I also recommend installing virtualbox from virtualbox.org and read the documentation while you are there.

You should install extension packs also.
Thank you

---

### Post by haqking on 2011-09-10
> **wildmanne39 said:**
> Hi, in virtualbox click on settings, then storage and your settings for storage should look basically like the screenshot.

I also recommend installing virtualbox from virtualbox.org and read the documentation while you are there.

You should install extension packs also.
Thank you

+1

I just took a screen dump of all the same thing to find you beat me to it ;-)

oh well useful for the future.

Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date depending on if you have the ppa added)

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following using terminal on your Linux box:
[I]
sudo usermod -a -G vboxusers username [/I]

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

Have fun

Regards

haqking

---

### Post by paker on 2011-09-11
Thanks for the replies. It is working now. What I did differently from previous attempt:
1) I used the most recent version from VirtualBox, not from synaptic package manager.
2) Used full XP, not upgrade version
Thanks.

---

### Post by ubudog on 2011-09-11
Moved to Virtualization.

Glad you got it working.  :-)

---

### Post by wildmanne39 on 2011-09-11
Hi, that is great I am glad you got it working.

---

