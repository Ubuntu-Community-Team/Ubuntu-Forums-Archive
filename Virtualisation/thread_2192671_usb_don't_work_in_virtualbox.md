---
title: "usb don't work in virtualbox"
date: 2013-12-09
forum: Virtualisation
---

### Post by spiridonios on 2013-12-09
hi
i m running ubuntu studio 13.04  kernel 3.8.0-34-lowlatency,
using virtualbox 4.2. 10
having installed windows xp 32-bit as my guest os

My problem is that the the guest os cannot recognize any usb device connected to any port of the pc. the ports are usb3, compatible with usb2 and the two front are usb2

in system--> users and groups --> manage groups I' ve added my user name to the vboxusers, vboxsf and lp groups.
I ve also have installed all the virualbox sidepacks from synaptic.
and the extension pack from virtualbox.org
VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.2.20
Revision:     90983
Edition:     
Description:  USB 2.0 Host Controller, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true
Why unusable:

any suggestions?

---

### Post by migs73 on 2013-12-09
If you have installed the virtual box from the repository (the open source version), it does not support USB. To get the USB support you have to download the version of virtual box from the oracle website(the private user licenced version but still free).

Mike

---

### Post by howefield on 2013-12-09
> **spiridonios said:**
> any suggestions?

What's the error when you try to enable a device, if you right click on the virtualbox USB icon, can you select the device ? 

> **migs73 said:**
> If you have installed the virtual box from the repository (the open source version), it does not support USB. To get the USB support you have to download the version of virtual box from the oracle website(the private user licenced version but still free).

This is no longer the case, for a while now both the repository version and the virtualbox website version are identical, both can use USB devices with the addition of the extension pack. There is no separate PUEL version.

---

### Post by spiridonios on 2013-12-09
mmm, weird.. I thought I've right clicked on the usb icon many times before.. could be that I had not

 anyway that's a relief! It's the first time i see my usb devices  attached, listed on a window when i right click on the usb icon. I  "ticked" two usb storage devices on the list. The windows pop up  notification and the unmount bar icon appeared but i couldn't really  open them and when i swiched on my scanner (it got also recognized in  the vb's usb icon menu) the guest Os "stucked" not allowing me to click  on ant button.

after restarting a couple of times the guest Os, and playing around with usb devices everything seems to work just fine! :grin:
I  think that opening a usb device in my host Os, then closing it and  "ticking" on the virtualbox 'es guest Os, helped in making the guest  recognising it..
Everything seems to work just fine. I hope it 'ii continue like this

Howefield your point turned to be really usefull!
Thank you guys!

---

### Post by migs73 on 2013-12-09
> **howefield said:**
> This is no longer the case, for a while now both the repository version and the virtualbox website version are identical, both can use USB devices with the addition of the extension pack. There is no separate PUEL version.

And I've been avoiding the one in the repository for ages!!

Thanks for the info.

Mike

---

### Post by howefield on 2013-12-09
> **spiridonios said:**
> Howefield your point turned to be really usefull!

Glad you got it sussed :)

> **migs73 said:**
> And I've been avoiding the one in the repository for ages!!

Well, there is another reason for getting the deb package from the website and that is version numbers. Even the current development version Trusty Tahr doesn't have the most recent Virtualbox version.

Just wanted to point out that the repository version isn't a barrier to getting USB support ect working.

---

