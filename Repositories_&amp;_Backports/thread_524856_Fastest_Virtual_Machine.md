---
title: "Fastest Virtual Machine ?"
date: 2007-08-13
forum: Repositories &amp; Backports
---

### Post by Frenezo on 2007-08-13
There are quite a lot of Virtual Machines out there, but I am suprised that there are not any benchmarks, so I have no idea which other VMs i should try[VMWare and VirtuaBox didnt work good for me!].


1) Shouldnt it be possible to benchmark VMs on a specific OS (like Windows XP) on a specific CPU type (like AMD Athlon X2 or Core 2 Duo)?

2) Which is the fastest VM on my machine (Athlon 64 X2, 2GB RAM, Host OS: Ubuntu Feisty, Guest OS: Windows XP) 

3) My ultimate goal is to run "Age of Empires 2" on it. Its kind of an old 2D game, but do u think its possible in an VM?

4) I consider using KVM with QEMU. Did anyone try that?



Thanks in advance!

---

### Post by MadMan2k on 2007-08-14
> **Frenezo said:**
> 
3) My ultimate goal is to run "Age of Empires 2" on it. Its kind of an old 2D game, but do u think its possible in an VM?
wine

---

### Post by Frenezo on 2007-08-15
> **MadMan2k said:**
> wine

wine does NOT properly run AOE2.

---

### Post by Mogurijin on 2007-08-17
It seems that Age of Empires 2 runs fairly well [in wine]("http://appdb.winehq.org/appview.php?iVersionId=147&iTestingId=11845").

---

### Post by zgornel on 2007-08-18
> **Frenezo said:**
> There are quite a lot of Virtual Machines out there, but I am suprised that there are not any benchmarks, so I have no idea which other VMs i should try[VMWare and VirtuaBox didnt work good for me!].


1) Shouldnt it be possible to benchmark VMs on a specific OS (like Windows XP) on a specific CPU type (like AMD Athlon X2 or Core 2 Duo)?

2) Which is the fastest VM on my machine (Athlon 64 X2, 2GB RAM, Host OS: Ubuntu Feisty, Guest OS: Windows XP) 

3) My ultimate goal is to run "Age of Empires 2" on it. Its kind of an old 2D game, but do u think its possible in an VM?

4) I consider using KVM with QEMU. Did anyone try that?



Thanks in advance!

Want went wrong with VMWare and VirtualBox ? Were they too slow or you encountered other problems as well ? AOE2 should run fine on them but, as he others mentioned, wine would be a very good alternative.

---

### Post by insane_alien on 2007-08-18
QEMUis very good if you have KVM capabilities on your processor. otherwise it is the same as the rest.

atm i preffer virtualbox as it seems to work more often than vmware and is slightly fast on my hardware.

---

### Post by Artemis3 on 2007-08-18
> **Frenezo said:**
> wine does NOT properly run AOE2.

Add backports, update wine to 0.9.41 and try again. And use the crack/no-cd whatever.

Yes, wine is always the fastest runner, so make it your priority to make it work there no matter what.

If you insist doing it the slow (compatible) way, install the lightest working OS. This game should run perfectly with win98, so install that in the virtualmachine, NOT XP. It should work fine with 64MiB of ram in the VM.

---

### Post by Frenezo on 2007-08-23
> **Mogurijin said:**
> It seems that Age of Empires 2 runs fairly well [in wine]("http://appdb.winehq.org/appview.php?iVersionId=147&iTestingId=11845").

Well its between "bronze" and "gold" i would call that good. I didnt even get Starcraft run with Wine properly althought it says "gold" (I tried 3different machines and 5different wineversions with different ubuntu versions)... I just want to say that wine has problems with 2D games, thats why I am looking for an alternative for old games.

**VMWare **has a choppy mouse on my machine (although I installed proprietary 3d driver for ati), so i dont even try to run strategy games.

**VirtuaBox **only allows me to have a 1024x768 resolution.

**QEMU **installs windows, but is VERY slow.

QEMU with **KVM **(as I have a new processor) doesnt even install WindowsXP. Even not with noacpi.

Looks like I am not mean to ahve a VM :(

If someone got the same problems: I got an Athlon X2 4800+ with 690G chipset on motherboard.

---

### Post by Super Jamie on 2007-08-25
Only 1024x768 in VirtualBox? You haven't set it up properly.

Boot up your Windows VirtualBox, and in the VirtualBox window choose Devices then Install Guest Additions. This adds a proper video driver so you can run your Windows desktop at any resolution, and don't need to "capture" the keyboard and mouse input.

You'll find VMWare Server will be quite choppy, as it passes all its' input and output through network code (as it's designed to run on a server, then you connect from your workstation via the console). VMWare Player is intended for desktop use, and as such it allows mouse and keyboard interaction directly with the VM. If you create your VM in VMWare Server, then run it in VMWare Player, you'll notice a difference in speed and responsiveness.

Don't forget to install VMWare Tools under Windows as well, this performs a similar function to VirtualBox Guest Additions.

As others have mentioned tho, the latest Wine backport is going to be your best bet.

I hope these help.

---

### Post by Vadi on 2007-08-28
My vote goes for VirtualBox too.

And I have no idea what did you search on Google, but a simple "virtualbox vs vmware vs qemu" search gives me the first result a benchmark comparison.

---

### Post by notwen on 2007-08-28
Always have had better luck w/ Virtualbox here.

---

### Post by ttbek on 2010-01-27
AOE2 supposedly works in WINE, though I haven't gotten it to work fully or at full speed myself....WINE takes a lot of tweeking.  I did get starcraft up and running, except for multiplayer and Battle.net though I here there is a way to do that to with WINE and some sort of patch.  I've been dual booting Win7 with my Ubuntu basically just for Starcraft, since the multiplayer is the important part for most Starcrafters.  I recently installed Virtualbox and a winXP, with the guest additions installation and 3d drivers, gave it as much video memory as I could and 3 gigs of ram, works great except that the mouse is slightly too unresponsive for the competitive world of Battle.net starcraft....not sure why, tried capturing the mouse and changing the windows XP settings, slightly better but still not precise enough, like it isn't sampling the mouse input at a high enough rate or something....  so I guess I'm sticking to the dual boot for now.

---

