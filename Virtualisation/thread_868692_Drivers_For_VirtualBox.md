---
title: "Drivers For VirtualBox"
date: 2008-07-24
forum: Virtualisation
---

### Post by rockstarrem on 2008-07-24
Hello,

I'm wondering if I can install drivers like I normally would in XP for inside of my VirtualBox or if theres a special way to do it? Could someone help me? Thanks!

Dom

---

### Post by hyper_ch on 2008-07-24
well, video card, motherboard, screen, sounds is all controlled by vBox... however other hardware that you attach to it through usb (printer, webcam, bluetooth, ....) require their own drivers in vBox

---

### Post by rcdeacon on 2008-07-24
If i'm not mistaken you CAN install the drivers. Once XP is up and running in virtualbox you can install programs, drivers, etc just as you would running XP natively.

---

### Post by rockstarrem on 2008-07-24
> **hyper_ch said:**
> well, video card, motherboard, screen, sounds is all controlled by vBox... however other hardware that you attach to it through usb (printer, webcam, bluetooth, ....) require their own drivers in vBox

So how could I install some ATi drivers to play games?

Dom

---

### Post by sdennie on 2008-07-24
> **rockstarrem said:**
> So how could I install some ATi drivers to play games?

Dom

As hyper_ch said, the video card is virtualized in the guest machine so, the guest (Windows in your case) isn't aware of the fact that you have an ATI card.  That basically means that you can't play games that rely on having hardware acceleration.

---

### Post by rockstarrem on 2008-07-24
And how about VirtualBox recognizing USB devices? Is this possible?

---

### Post by mlentink on 2008-07-24
Yes, but not in the OSE (Open Source Edition) that you may have found in the repositories. USB is supported in the closed source (but free) version you will find on the VBox site

---

### Post by philinux on 2008-07-24
Then you need to install the Guest Additions.

You'll need to read the Vbox pdf manual.

---

### Post by rockstarrem on 2008-07-24
> **philinux said:**
> Then you need to install the Guest Additions.

You'll need to read the Vbox pdf manual.

I installed the guest additions but have no idea what to do next.

---

### Post by mlentink on 2008-07-24
Applications>System Tools>VirtualBox 
will allow you to configure your virtual machine, including the USB properties (if you installed the closed source version. The open source edition does not support usb)

Edit: the vm must obviously be switched off to be able to change configurations!

---

### Post by rockstarrem on 2008-07-24
I installed the open source version, damn, is it a flawless switchover or will I need to reinstall Windows and all that?

---

### Post by bodhi.zazen on 2008-07-24
> **rcdeacon said:**
> If i'm not mistaken you CAN install the drivers. Once XP is up and running in virtualbox you can install programs, drivers, etc just as you would running XP natively.

No, you need to be very careful with that. Well, not too careful, it is a virtual OS :lolflag:

Virtualization works by emulating your cpu, hard drive, network card, videocard, etc. The guest does not use the ATI drivers, for example, as it does not have (emulate) an ATI card.

The additional drivers are on the Addons.

I have found upgrading versions of Virtual box *usually* goes without problems, but occasionally there can be issues.

The most common issue I find is with snapshots. You need to elimate / merge snapshots b4 upgrading.

---

### Post by rockstarrem on 2008-07-24
I don't have any snapshots, is it worth a shot?

---

### Post by rockstarrem on 2008-07-24
New problem: I mount a CD Rom image and it doesn't show up in My Computer. I don't know what to do here.

---

### Post by rockstarrem on 2008-07-24
I've ran into a problem with upgrading, when I start a VirtualBox I get this error:

> 
00:00:02.475 VirtualBox 1.6.2 r31466 linux.x86 (May 31 2008 18:32:14) release log
00:00:02.475 Log opened 2008-07-24T22:40:00.508339000Z
00:00:02.488 Support driver version mismatch: DriverVersion=too-old ClientVersion=0x70002
00:00:02.489 ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={d5a1cbda-f5d7-4824-9afe-d640c94c7dcf} aComponent={Console} aText={The VirtualBox support driver which is running is from a different version of VirtualBox.  You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
00:00:02.489 VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH)} aWarning=false, preserve=false
00:00:02.494 Power up failed (vrc=VERR_VM_DRIVER_VERSION_MISMATCH, hrc=NS_ERROR_FAILURE (0X80004005))



I've completely removed the old installation and hard disk (of Windows XP virtual). Can anyone help?

---

### Post by lottes70 on 2008-12-17
I'm having this problem. I had an old version, 1.5.6 IIRC, installed, and installed the 2.1.0 OSE edition, and now I get this same message.

So this is basically a bump...

---

### Post by inobe on 2008-12-18
just so everyone knows, 3D acceleration with opengl is experimental in vbox starting with version 2.1, later on direct 3D will be implemented, it will actually use the host video adapter,  as of now it is disabled and the hardware is emulated.

from my understanding' only windows guests can benefit from 3D acceleration.

---

