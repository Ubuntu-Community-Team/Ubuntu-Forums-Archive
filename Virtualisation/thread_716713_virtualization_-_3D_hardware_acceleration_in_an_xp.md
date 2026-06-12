---
title: "virtualization - 3D hardware acceleration in an xp home child"
date: 2008-03-06
forum: Virtualisation
---

### Post by pompeyjohn on 2008-03-06
Hello there,

I have a quick question about virtualization and 3d graphics. There are many confusing posts and articles. I hope somebody can please clarify the situation.

I have an application which will only run in Windows. It is called Phoenix and is a simulator for Radio Controlled helicopters. I believe that it makes heavy use of DirectX. It also has a proprietary USB dongle.

I would like to run this application in an XP Home child of an Ubuntu host. The laptop I have targeted for this has the following specifications.

Dual core CPU’s both running at 2 Ghz
4 GB ram
Nvidia graphics card with 1 GB ram

Which virtualization program can I use to make this work as smoothly as possible? I am led to believe that emulation or WINE is not feasible. I have hard disk space and ram to spare so happy to dedicate a child machine for this singular purpose.

So far I am aware of the following virtualization options….

Virtualbox
VMware

I understand that Virtualbox maybe quicker, but has poorer USB support. It also appears that VMware may have 3d graphics acceleration? But all the information I read about this suggests it is only for Macs?

I am so confused. Somebody please help.

Thanks in advance,
John

---

### Post by luisromangz on 2008-03-06
As far as I know, there isn't any virtualization packages that offer graphics acceleration to the guest system.

---

### Post by mozetti on 2008-03-06
Another potential issue is the proprietary USB dongle. If Ubuntu can't properly recognize the device then it won't be able to provide it to the child machine, regardless of the vitrualization software used.

---

### Post by pompeyjohn on 2008-03-06
yes agree - regarding the dongle. Hopefully it will work. 

Without 3d acceleration I can not get to the point of checking it will work or not though.

---

### Post by Daveski on 2008-03-06
Sounds like you will have better luck dual-booting - or you could ask Runtime to break away from the proprietory DirectX and move to OpenGL, and even if they could port a Linux version. No harm in asking.

---

### Post by Meatshield on 2008-03-06
3D hardware acceleration is in its infancy with virtualization. If you try to turn on desktop effects in an Ubuntu VM for instance it can't do it. I think VMWare has a beta option for hardware acceleration, but I wouldn't advise doing it. I haven't managed to get it working so far.

---

### Post by fjgaude on 2008-03-06
From what I know about 3D it seems we are quite aways away from having it in virtual. The issue is the hardware: how to emulate complex graphic chips like we do mouse, keyboards, and USB ports? Can we emulate a CPU; I don't think so, ecept to translate its code. That's where many programmers stand right now with DirectX.

VMware is trying and likely will be the first there. But it seems only the gamers are the ones who need it, not the ones in the business world, not even the graphic designers like me. <smile>

---

### Post by pompeyjohn on 2008-03-07
Thank you all. Much appreciated.

I'll keep an eye out for news and if I hear anything will post it here.

---

### Post by bbhavsar on 2009-08-04
VMware support DirectX 9c for Windows guests including XP and Vista.

You could use VMware Workstation/Player for Linux. [http://www.vmware.com/products/ws/](http://www.vmware.com/products/ws/)

Hope that helps...

---

