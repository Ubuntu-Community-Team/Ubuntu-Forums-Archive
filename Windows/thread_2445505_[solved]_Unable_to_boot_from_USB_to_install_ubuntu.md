---
title: "[solved] Unable to boot from USB to install ubuntu - Windows 10 (legacy mode)"
date: 2020-06-15
forum: Windows
---

### Post by gattopazzo23 on 2020-06-15
Hi there,
So I just bought this pc with Windows 10 Pro installed, for gaming. I was going to keep on using my old laptop with Ubuntu for serious stuff but it broke, so now I wish to dual boot Windows and Ubuntu on the new pc.

I downloaded the Ubuntu ISO, created a bootable usb with Rufus, but now I can't access the BIOS to boot from the USB and install Ubuntu.

I press F2 or Des as instructed on the "Asus" screen before Windows loads, but nothing happens.

I searched the internet, and found instructions, but all of them were about entering the BIOS mode on a UEFI machine. Unfortunately, my PC is in Legacy Bios mode with an MBR partition, so I don't know what to do. For example, they said to press the restart button on the "start" menu while holding the "shift" key, and explained how to open the "UEFI and firmware settings" "from there, but there is no "UEFI and firmware settings" menu on my pc, obviously (i suppose?) because Windows is installed in Legacy mode.

Thanks much for reading this,

Leonardo

---

### Post by CelticWarrior on 2020-06-15
It must be a very old computer to have BIOS. Any factory installed Windows 8 or newer is in UEFI PCs and in UEFI mode as it should be. 
And if really that old then the "for gaming" becomes a bad joke, honestly.

Or is it actually a second hand new(ish) computer in which the previous owner, an idiot, forced a legacy installation in a UEFI PC? If so, if it was mine and I wanted to dual-boot, the first thing I would do is a proper Windows 10 installation in UEFI mode. And then Ubuntu the same way, obviously.

Now, regardless of previous considerations and irrespective of the mode the OS or OSes was/were installed, users shoukld ALWAYS be able to access the firmware, BIOS or UEFI. If you can't you're doing something wrong like pressing the wrong key (or keys) or not pressing it fast enough. Also some new and new(ish) UEFIs allow swapping the usual F keys functions to their secondary functions, something that before would require FN+F... . You may need - and I've found some with that setting by default - FN+F2 instead of F2. And always spam the key, whatever that is, even before the splash screen appears.

---

### Post by C.S.Cameron on 2020-06-15
I recently tried using mkusb-plug to make a Windows 10 installer:
[https://askubuntu.com/questions/1250481/bootable-usb-not-detected-in-bootloader/1250530#1250530](https://askubuntu.com/questions/1250481/bootable-usb-not-detected-in-bootloader/1250530#1250530)
It worked great in BIOS mode.
I understand that Rufus will also make a Windows 10 installer that works in BIOS mode as long as you select MBR, BIOS.

---

### Post by gattopazzo23 on 2020-06-16
> **CelticWarrior said:**
> 
Or is it actually a second hand new(ish) computer in which the previous owner, an idiot, forced a legacy installation in a UEFI PC? If so, if it was mine and I wanted to dual-boot, the first thing I would do is a proper Windows 10 installation in UEFI mode. And then Ubuntu the same way, obviously.


It's actually a fairly new computer. I have no clue why the builder installed bios, really. It's not the only stupid thing that guy did, he also installed a terrible Itek cheap-ass PSU that I'm going to change (I'm a noob so I didn't know that until a friend of mine pointed that out to me). But now I somehow managed to access bios just by trying much more times the F2 button. Don't know why it didn't work before.

Thank you anyway for replying, saludos

Leonardo

---

### Post by CelticWarrior on 2020-09-02
> [COLOR=#000000]Don't know why it didn't work before.[/COLOR]

It didn't because you weren't doing it right or quick enough. It happened to all of us at least once.

---

