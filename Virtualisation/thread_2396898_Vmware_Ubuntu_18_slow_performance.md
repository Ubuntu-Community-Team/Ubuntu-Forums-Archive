---
title: "Vmware Ubuntu 18 slow performance"
date: 2018-07-22
forum: Virtualisation
---

### Post by khan3 on 2018-07-22
Hi,

Ive recently installed ubuntu 18 on my vmware. Giving it 8 processors and 11 gigs of memory, but yet it is still noticeably laggy/slow.

I have the same settings with an Ubuntu 14 on vmware which works smoothly.

I do remember this also being the case initially on my ubuntu 14.04 but after installing/updating some software it went to being smooth. I just can't remember what i did.

As far as im aware i have vmware tools installed, can you think of anything else i need to do when first using Ubuntu in a virtual machine to improve performance?

thanks

---

### Post by stardawg on 2018-07-22
> **khan3 said:**
> Hi,

Ive recently installed ubuntu 18 on my vmware. Giving it 8 processors and 11 gigs of memory, but yet it is still noticeably laggy/slow.

I have the same settings with an Ubuntu 14 on vmware which works smoothly.

I do remember this also being the case initially on my ubuntu 14.04 but after installing/updating some software it went to being smooth. I just can't remember what i did.

As far as im aware i have vmware tools installed, can you think of anything else i need to do when first using Ubuntu in a virtual machine to improve performance?

thanks

you have to sudo apt-get install open-vm-tools-desktop.

---

### Post by khan3 on 2018-07-28
@stardawg i already have this installed

Reading package lists... Done
Building dependency tree       
Reading state information... Done
open-vm-tools-desktop is already the newest version (2:10.2.0-3ubuntu3).
0 to upgrade, 0 to newly install, 0 to remove and 37 not to upgrade.

---

### Post by canartuc on 2018-08-27
You need to update graphic card settings too - AFAIK, your machine is strong enough to handle ubuntu 18 in vm. If your graphic card is good enough, you can make the things much more powerful but even if it is not, you need to play around the settings inside Display section. Normally I allow vmware to use 3D acceleration with 768mb of graphic memory so everything is so smooth as using native.

---

