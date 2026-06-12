---
title: "Slow games and flash when using VBox (Ubuntu guest, Vista host) 100% CPU usage"
date: 2009-07-29
forum: Virtualisation
---

### Post by EndersJ on 2009-07-29
Hi all,
I'm rather new to Ubuntu but enjoying it so far. 
I run Ubuntu 9.04 as guest through VirtualBox on a Vista host. When running any emulators (e.g. ZSNES), any flash (e.g. YouTube),  or music programs (e.g. LMMS), I get extreme lag and 100% CPU usage making these programs unusable.

I've been reading a lot of threads and tried a lot of the fixes out there including:
-Running another virtualmachine (one that booted or one that just sat at the "No bootable media found")
-Devoting more RAM (went as high as 1008MB), video memory (went as high as 128MB)
-I tried disabling/enabling 3D acceleration

I downloaded all the recommended updates when the OS first installed, I also downloaded flash with:

```
sudo apt-get install flashplugin-nonfree
```and powernowd with:

```
sudo apt-get install powernowd
```Can anyone help me figure out how to correct this? I feel like these game (especially the SNES emulator) should work fine with the computing power I am devoting to it, so my guess is its some drivers or something I need to download, I'm just not sure which ones. I have an older crap computer running ubuntu and ZSNES works fine on it, this is why I believe it is a driver issue possibly related to VirtualBox. 

PLEASE HELP!! Thanks.

Specs:
HP Pavilion dv2000
2GB RAM
Intel CoreDuo CPU T2450 @ 2.00 GHz  2.00 GHz
Vista Home Premium (32-bit)

Running Ubuntu 9.04 (Jaunty) as a guest on VirtualBox 3.0.2 r49928.

---

### Post by bear24rw on 2009-07-29
do you have a virtualization option in your bios? if you do perhaps you can try enabling it?

---

### Post by EndersJ on 2009-07-29
> **bear24rw said:**
> do you have a virtualization option in your bios? if you do perhaps you can try enabling it?
 
Thanks for the quick response bear and great suggestion, I have not come across this fix before. But unfortunately I have checked and my BIOS has no such virtualization or VT option.

---

