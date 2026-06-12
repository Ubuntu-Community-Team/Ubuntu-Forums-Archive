---
title: "Booting the same Ubuntu installation as a guest of Windows, and as native"
date: 2010-03-15
forum: Virtualisation
---

### Post by Cato2 on 2010-03-15
Not sure if this is easily done, but my situation is that I have a fairly complex Ubuntu 8.04 setup which I use for everything except for Windows 3D games that don't run on WINE / Crossover Games.  I've tried VMware but it doesn't run most Windows games due to DirectX.

So... I still need a Windows XP partition to run some games natively (including Metaboli for game rental), and I want to keep my current Ubuntu setup.  What I'd like to do is be able to boot in two ways:

1. Windows XP native for certain 3D games only - hosting an Ubuntu VM using my existing Ubuntu setup via raw disks. The idea is that all my current Ubuntu apps and data are available in the VM, with games running on native XP.

2. Ubuntu native, with no Windows (except perhaps a separate Windows VM - mostly I can use WINE or Crossover) - for all other activities including some 3D games.  Must use the same raw disks as (1).

Clearly the hardware environment will look very different for Ubuntu in cases 1 and 2.  I need the equivalent of Windows hardware profiles...  The most challenging parts are likely to be the names of boot disks etc, though as I'm using ext3 FS labels and LVM volume names I may be able to avoid that.  Also the modules loaded and xorg.conf will be completely different.

I'm wondering if there are any HOWTOs about this - not necessarily for Ubuntu.

I will probably upgrade to Windows 7 soon, so solutions depending on that are fine, but I think this is mostly an Ubuntu issue.

I can use either VMware Server or Virtualbox if that helps.

---

