---
title: "&quot;Dummy Output&quot; sound"
date: 2011-08-26
forum: System76 Support
---

### Post by khuffmanjr on 2011-08-26
After a few days of using my new Serp7 my sound just crapped out and left behind a Dummy Output device that produces nothing.  I have experienced this before on my desktop and the issue is, as of yet, unresolved on either machine.  I don't really care about the desktop though so I've only just started looking into this problem that has now cropped up on my new laptop.

"lspci -v" output includes:
```
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device 5102
    Flags: bus master, fast devsel, latency 0, IRQ 3
    Memory at f6500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel
```Ubuntu 11.04
Unity or Classic Gnome
The issue started after installing VMWare Workstation, though sound worked for some time after that
The issue started after switching to Classic Gnome.  Sound was untested after this.
The issue started after a failed "umount -f" of a nfs export, I had to "umount -l".  Sound was untested after this.
The issue was noticed after resuming from suspend.

That's about all I can think of.  So I would appreciate any help.  Thanks!  :)

---

### Post by khuffmanjr on 2011-08-26
Nevermind, I found the solution and it was quite easy.  Check the sound problem guide sticky in the Multimedia and Video section on these forums.

```
sudo modprobe snd-hda-intel
```
note: this is the driver for my system and it may not work for you.

I'll ensure this loads with every boot and hopefully all is well.

Thanks if you looked at my question.

---

