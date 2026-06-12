---
title: "how to make ment2 boot from LiveUSB?"
date: 2014-03-16
forum: System76 Support
---

### Post by tlroche on 2014-03-16
I have a LiveUSB drive from which I can boot my laptops (an S76 and a ThinkPad). It's past time a friend upgraded her Meerkat (model=ment2), so I tried booting it from the LiveUSB ... and failed. This seems odd, because I know I have previously installed Ubuntu and Mint on this ment2 from its external USB CD/DVD player (it does not have internal CD/DVD).

Note also that the ment2's motherboard (a Zotac with AMI BIOS) does not have a separate boot-order menu (per Ian Santopietro in 2011), as with my laptops. Instead, I did the following:

1. Power down (`sudo shutdown -Ph now`), power up.

2. At the Zotac splash screen,

2.1. hit key=Del to enter AMI BIOS
2.2. enter supervisor password
2.3. insert LiveUSB

3. In the BIOS,

3.1. mainmenu>Boot>Boot Device Priority
3.2. here I assumed I would see at least 2 boot devices (HD and USBD), and I would ensure the USBD was first in boot order. Instead, I only saw the HD available.

4. Exit BIOS, boot selected device.

So I'm wondering, how to fix? I searched this forum and noted [this subthread]("http://ubuntuforums.org/showthread.php?t=2189074&p=12865024#post12865024"), in which a similar problem is caused when the OP's netbook has an SD card in its slot. The ment2 doesn't have that problem, but I know that it has a USB keyboard and wireless mouse. I know neither peripheral shipped with the ment2, but I don't know if I installed from the USB CD/DVD before or after the current peripherals arrived :-( and I also know that I can't drive the BIOS without a keyboard.

So I'm wondering: do I need to hunt down a PS/2 keyboard to troubleshoot why I can't boot the USB drive? Or is there something else I can try first?

---

### Post by tlroche on 2014-03-17
> **tlroche said:**
> I searched this forum and noted [this subthread]("http://ubuntuforums.org/showthread.php?t=2189074&p=12865024#post12865024"), in which a similar problem is caused when the OP's netbook has an SD card in its slot. The ment2 doesn't have [an SD card reader], but I know that it has a USB keyboard and wireless mouse. I know neither peripheral shipped with the ment2, but I don't know if I installed from the USB CD/DVD before or after the current peripherals arrived

However I did verify today that I **can** boot from a gparted LiveCD via the ment2's external USB CD/DVD reader: BIOS recognized it and allowed me to set it first in the boot order. FWIW, that reader is 2-headed (presumably for power draw), but I kinda doubt that (i.e., the difference between a normal 1-headed USB-connected drive and a 2-headed USB-connected media reader) could cause differential outcome. Am I missing something?

So to summarize:

1. (problem) LiveUSB is not recognized @ boottime by ment2.
2. same LiveUSB is recognized @ boottime and is booted by laptop.
3. LiveCD in USB-connected CD/DVD reader is recognized @ boottime and is booted by ment2.

---

### Post by tlroche on 2014-03-25
Eventually I escalated to System76 support. Net: I'll just hafta burn a LiveDVD to do the install.

---

