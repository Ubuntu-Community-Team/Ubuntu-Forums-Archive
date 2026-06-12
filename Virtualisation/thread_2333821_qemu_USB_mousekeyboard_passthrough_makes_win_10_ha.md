---
title: "qemu USB mouse/keyboard passthrough makes win 10 hang at boot"
date: 2016-08-13
forum: Virtualisation
---

### Post by galun on 2016-08-13
So, I set up my computer for GPU passthrough, with UEFI and VirtIO drivers and all that, pretty much exactly like this guide [https://bufferoverflow.io/gpu-passthrough/](https://bufferoverflow.io/gpu-passthrough/) with a few minor tweeks for ubuntu.

Problem is that after I've installed Windows 10 it hangs at the boot screen unless I remove the options for USB passthrough. The mouse and keyboard I passthrough works fine during the installation of Windows 10, but not when it tries to boot after installation.

I've tried my regular mouse/keyboard combo, wireless logitech. I've tried just a mouse, wired from Microsoft. And just a keyboard, also wired and from microsoft. They all make it freeze at the boot screen.

Finally I tried an xbox one controller just to see if it was all USB devices or just mouse and keyboard. It does boot with the xbox one controller, at least when I use the -M q35 option with qemu. It also boots without -M q35 as long as I don't use any USB passthrough. But I obviously can't do anything since I have no mouse or keyboard.

Best info I found so far is that Windows 10 fastboot screws up when using UEFI, but since I can't do anything in win I've not been able to disable it to test if that is the problem. Also win 10 seem to require that you have a working win 10 in order to boot into safemode (stupid).

If I can't get this to work my only option would be to make a UEFI bootable win 7, but I'd really prefer win 10 on this. So if anyone have any good ideas I could try that would be great.

---

### Post by KillerKelvUK on 2016-08-13
Hey so I had a similar issue I believe but instead of a hang I got a reboot loop. Detach the USB devices and all okay, however to clear up the bad config from all the borked (re)boots I had to take Windows into safe mode and then do a clean shutdown from here. Windows would then start properly and complete a boot to desktop (without USB devices attached). My solution was to attach post boot but this may not be what you want sorry, I didn't ever find a proper fix.

If all you want its keyboard and mouse then I'd suggest you take a look at Synergy, great solution for sharing a single K&M between host and guests.

---

### Post by galun on 2016-08-14
Yeah, right now all I want is a keyboard or mouse to work, maybe I'll be able to do something in Win that stops the hangup. Thanks, I'll have a look at Synergy.

Thanks for the other suggestion too, by now even a dirty workaround would be nice. I'm currently trying to use another VM to set it up, then hopefully I can use the image created with qemu once it's setup and maybe that will work. If that won't work I'm gonna try to use virt-manager to attach the USB devices after it's booted, I don't know how I'd do that by using qemu command line, all though I'm sure there is a way and I'd prefer it if I could put it in a script.

Back to reading manuals and whatnot, feel free to throw me more suggestions.

---

### Post by KillerKelvUK on 2016-08-14
Hey, you can use the qemu console/monitor to managed the guest from the host including adding and remove usb devices, see here... [https://en.wikibooks.org/wiki/QEMU/Monitor](https://en.wikibooks.org/wiki/QEMU/Monitor)

---

### Post by galun on 2016-08-16
Thanks for the help guys. It turned out that it wasn't just the USB devices but also the GTX1080 card that was causing problems. The solution was to use a diffrent bios file from the one I had, when using the one from here [https://sourceforge.net/projects/edk2/files/OVMF/](https://sourceforge.net/projects/edk2/files/OVMF/) all the problems went away and now I'm using HTC Vive on it and everything.

---

### Post by KillerKelvUK on 2016-08-17
> **galun said:**
> Thanks for the help guys. It turned out that it wasn't just the USB devices but also the GTX1080 card that was causing problems. The solution was to use a diffrent bios file from the one I had, when using the one from here [https://sourceforge.net/projects/edk2/files/OVMF/](https://sourceforge.net/projects/edk2/files/OVMF/) all the problems went away and now I'm using HTC Vive on it and everything.

Glad you have this sorted, just for reference that OVMF source you linked is ancient, I'd instead recommend either the ubuntu ovmf package (if using 16.04) or grab one of kraxel's nightly builds [https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/).  Its possible you will have other subsequent issues with such an old ovmf build.

---

