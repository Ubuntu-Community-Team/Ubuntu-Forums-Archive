---
title: "new ubuntu server installation puts monitor in standby mode"
date: 2010-04-13
forum: Server Platforms
---

### Post by MonkeyZiggurat on 2010-04-13
I just installed ubuntu 9.10 server edition (twice, just to be sure) and the installation ran fine, but when I try to boot into the system, i get past the BIOS loading screen then my monitor just goes into power saving mode and I can't get it to see a signal from the PC. I know the OS is running, because I can ssh into it from my laptop, and I know the monitor works, because that machine had a windows OS on it before and that worked fine with the same monitor. I had thought it might be a graphics card thing with ubuntu trying to push out at a resolution not supported by the monitor, but I find that unlikely as it's brand new this month. If anyone has any idea of something I can try to diagnose the problem, that would be great. As I said, I still have ssh access to the PC, so I can basically try anything on it that I could if I was physically at the box itself.

Any and all help would be much appreciated.

---

### Post by volkswagner on 2010-04-13
What's brand new this month?  If it's your graphics card, then it may not be supported yet.

Check logs

```
 cat /var/log/Xorg.0.log
```

---

### Post by MonkeyZiggurat on 2010-04-14
Sorry, I meant the monitor is brand new, the PC is actually quite old. I checked for that logfile and it doesn't seem to exist on my system at all...I also don't have an Xorg.conf file in /etc/X11 That could be normal for Server edition for all I know, I've only ever used the standard Ubuntu till now.

---

### Post by volkswagner on 2010-04-14
Sorry, my bad.

Perhaps the monitor is too sensitive.  Have you tried power cycling the monitor, while also giving keyboard input?

You may find some info with dmesg or syslog.

Sorry I can't be more help...

Have you tried with a different monitor?

I had a Dell monitor that would sleep very quickly.

Also, do you have multiple video out ports on your card/machine?  Perhaps it is not defaulting to the one you wish.

---

### Post by MonkeyZiggurat on 2010-04-14
Thanks for the reply. I found this in syslog. It has something to do with the graphics card, could be a clue as to what's going on:

Apr 13 19:06:37 nix02 kernel: [    1.405468] Linux agpgart interface v0.103
Apr 13 19:06:37 nix02 kernel: [    1.408934] agpgart-intel 0000:00:00.0: Intel 865 Chipset
Apr 13 19:06:37 nix02 kernel: [    1.409070] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Apr 13 19:06:37 nix02 kernel: [    1.410677] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
Apr 13 19:06:37 nix02 kernel: [    1.518233] usb 4-1: new low speed USB device using uhci_hcd and address 2
Apr 13 19:06:37 nix02 kernel: [    1.531356] [drm] Initialized drm 1.1.0 20060810
Apr 13 19:06:37 nix02 kernel: [    1.545925] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 13 19:06:37 nix02 kernel: [    1.545932] i915 0000:00:02.0: setting latency timer to 64
Apr 13 19:06:37 nix02 kernel: [    1.559554] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
Apr 13 19:06:37 nix02 kernel: [    1.559558] Copyright (c) 1999-2006 Intel Corporation.
Apr 13 19:06:37 nix02 kernel: [    1.559609] e1000 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 13 19:06:37 nix02 kernel: [    1.776752] FDC 0 is a post-1991 82077
Apr 13 19:06:37 nix02 kernel: [    2.023267] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:56:26:cc:bc
Apr 13 19:06:37 nix02 kernel: [    2.032315] [drm] fb0: inteldrmfb frame buffer device
Apr 13 19:06:37 nix02 kernel: [    2.032329] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 13 19:06:37 nix02 kernel: [    2.127080] render error detected, EIR: 0x00000010
Apr 13 19:06:37 nix02 kernel: [    2.127085] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
Apr 13 19:06:37 nix02 kernel: [    2.127091] render error detected, EIR: 0x00000010
Apr 13 19:06:37 nix02 kernel: [    2.133705] [drm] TMDS-7: set mode 1366x768 1b
Apr 13 19:06:37 nix02 kernel: [    2.147866] Console: switching to colour frame buffer device 170x48


There was something very similar in dmesg as well. Is the graphics card just screwed? I seem to remember Ubuntu server 8.04 didn't come with a gui, so I might try that out and see what happens.

---

### Post by iissmart on 2010-04-15
Try switching to different virtual terminals just for kicks. Hold ctrl+alt and cycle through pressing F1, F2, F3, F4, etc, wait ~5-10 seconds to see if anything appears then try the next one. If things are working properly, you'll see a text login prompt at some point. This will at least rule out your xorg settings, but it still could be a hardware issue (video card, monitor).

---

### Post by MonkeyZiggurat on 2010-04-16
Thanks for the replies. The other virtual terminals were a no-go, so I thought I might as well try upgrading to the 10.04 beta. No luck there either. I've installed Ubuntu 8.10 Server, which is just fine. I guess I don't need a desktop environment anyway, it's only a fileserver. Sort of feels like giving up, but I'm pretty sure it's down to some piece of goosed hardware, so I don't feel that bad. Anyway thanks for the help.

---

