---
title: "[SOLVED] virtualbox-ose-modules-2.6.24-20-generic broken package?"
date: 2008-09-15
forum: Virtualisation
---

### Post by oedo808 on 2008-09-15
I get:
The following packages have unmet dependencies:
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
E: Broken packages

I've done
sudo apt-get update
sudo apt-get install virtualbox-ose-modules-generic
sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic

I put in uname -r and apparrently my kernel is 2.6.24-19-generic...

Sorry I'm very new to Linux if my terminology is off... so anyways i put in
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
and it works fine... so is that a bug in apt-get I guess?  do I need to report it or anything?

I'm extremely excited to get virtualbox installed!! I've been through 3 distributions trying to find the easiest one to get ndiswrapper installed after jacking around with Fedora 9 for 3 freakin days unable to install ndiswrapper... I went with Ubuntu and i love it, not only is it significantly smaller but it seems like a much friendlier distribution.  Anyways, this is my first post to the Ubuntu forums, and it's probably in the wrong place b/c I answered my own question but I'm too happy to care right now :).

Thanks everyone.

---

### Post by overdrank on 2008-09-15
Hi and welcome, moved to Virtualization :)
Hi and the error indicates broken packages so you may open synaptic manager and fix any broken packages under edit.

---

### Post by oedo808 on 2008-09-15
Thanks for moving my topic.  So I have Windows XP installed on my VirtualBox guest and it doesn't have the VMware PCNet network drivers.  I think I have the drivers but I cannot seem to get them on the guest.  I have a shared folder set up, but net use won't work because it knows I'm not connected to a network.. I tried plugging in a USB stick but the guest doesn't notice it has been plugged in... Is there something I need to enable in VirtualBox for it to pass along my USB hardware info to the guest?

Thanks for the help!

---

### Post by bpalone on 2008-09-16
You might want to go to Sun Microsystems site and download the non-open source version.  I think they are up to Version 2 point something now.  I use 1.6.2 and it works with most USB devices.  If I remember correctly the open source version doesn't support USB.

The non-open source version is still free for personal use or evaluation.  Their personal use interpretation is quite liberal.

Here is link to their site: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Good luck and welcome to Linux and Virtual Machines.

---

### Post by oedo808 on 2008-09-16
Hey, thanks for the help you guys... I don't think I need to be too concerned with USB support, I realized that getting the network drivers over to the guest was as simple as writing them to an .iso and mounting them... from there I'll just file share... I really only need xp for compatibility b/c i'm using the laptop for class in an all XP school.

---

