---
title: "Virtualbox- two questions"
date: 2009-06-18
forum: Virtualisation
---

### Post by blur xc on 2009-06-18
I installed virtualbox and I have vista running inside of it.  So far, so good, but I've got two issues (so far)...  

#1- how do you share a folder between ubuntu and vista?  I clicked on share folder, and I added one.  In vista, I press <right-ctrl> - <home> and it shows up on my devices menu but I don't know what to do from there.

#2- how do I see my usb ports?  I can't figure that one out...

I installed the guest services pack (I think I did it right)...  Is it supposed ot install inside of yor guest os?  It just seemed strange to me...  

Anyway, thanks...

BM

---

### Post by blur xc on 2009-06-18
D'oh!  I found this- [http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host) which kind of explains why I can't see my usb ports on my virtual machine.  I would imagine that it's not that different for 9.04.  So- the new question is how to change the version of virtual box I have installed w/o killing my vista setup...

BM

---

### Post by clive littlewood on 2009-06-20
Hi

Download the latest deb file from the sun site (I use the Beta 1)

Virtualbox-3.0_3.0.0_BETA 1-48728_Ubuntu_jaunty_i386.deb

Before you open and install remove the previous version from synaptic, but only use the remove and not completly remove option.

This will leave all your config files in place.

This version will give you full USB usage.

Hope this helps

Clive        ):P

---

### Post by blur xc on 2009-06-21
> **clive littlewood said:**
> Hi

Download the latest deb file from the sun site (I use the Beta 1)

Virtualbox-3.0_3.0.0_BETA 1-48728_Ubuntu_jaunty_i386.deb

Before you open and install remove the previous version from synaptic, but only use the remove and not completly remove option.

This will leave all your config files in place.

This version will give you full USB usage.

Hope this helps

Clive        ):P

Ok, I did all that and it worked great- until today.  thanks, the fix was easy and surprisingly fast.

I don't think I changed anything, but today I can't see my usb ports on my guest machine.  I pull down devices->usb and they are there but greyed out.

BM

---

