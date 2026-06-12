---
title: "Problems with Virtualization Manager in UBUNTU"
date: 2008-10-16
forum: Virtualisation
---

### Post by tux-fan on 2008-10-16
I downloaded Hardy 64 bit a few days ago and attempted to use the built in Virtualization Manager.  My experience has been nothing but miserable.  I installed windows 2000, but when the virtual machine rebooted the system was not able to connect to the CDRom.  It turns that the CDRom was not left configured into the Virtual manager. No the Windows OS will not start because it can't load SP2 which was included on the CD.  I have spent severals days trying to configure a CD in the virtual manager, but have been unsuccessful.  

My most recent attempt was to upgrade the virtual manager from 0.5.3 that included with the distribution to see if this bug has been fixed. I can't do this because the pygtk2 package is not installed and I cannot figure out how to resolve this requirement.  I have spent so much time doing this and so disappointed in the poor support choices offered by the virtual manager product.  I would pay, but I don't know who to pay.  This has been too costly (in terms of my time) for me to implement.  Is there a solution to this mess or should I move on to a different product?

---

### Post by caver1 on 2008-10-16
I am running Hardy 64 bit with win 200o virtualized with no problems. When you say Ubuntu's Virtualization Manager.Are you talking about Virtual Box?
If you are there are settings In Vbox to help. When you open Vbox Highlight the OS you want to start then click on settings you will see cdrom there. 
If you are using Vbox OSE you might want to go to the Vbox web site and install the PUEL version of Vbox. It is better and has a few more features. You can add their repositories to Synaptic to keep it updated.
caver1

---

### Post by tux-fan on 2008-10-17
I am talking about the Virtual Manager that can with Ubuntu.  Version 0.5.3 is in the repository and I can't get it to work or upgrade to a newer version or install a CD in the current version.

---

### Post by jfkuhn on 2008-10-30
Hi, are you still having an issue with this?  I believe you are talking about Virtual Machine Manager ver. 0.5.3  As I understand it, the new version (0.5.4) does indeed solve some of these problems, but is only available on the next release (Intrepid), see this post:

[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/238692]("https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/238692")

I have just set up a VM on Hardy (I have done this before in Fedora 8 and it seemed a lot easier, but it still was a little buggy), and it seems to be working.  I am still having trouble accessing the CD ROM or the internet (which again was not the case in my Fedora VM, which allowed me to access all the media on my system and the internet.  I'm not sure what is different now).

While I need to work the bugs out of this, I do have a windows machine running under VMM.  According to the bug, you can't create a drive for the CDROM.  But what I did was to assign the CDROM as an image to an .iso of the Windows install disk.  This allowed the .iso image to be "mounted" like a CDROM and WinXP finished its install that way.  You could perhaps assign an image of SP2 to the CD drive and it may get you through.  I hope that helps (because I'm kind of a newb)

---

