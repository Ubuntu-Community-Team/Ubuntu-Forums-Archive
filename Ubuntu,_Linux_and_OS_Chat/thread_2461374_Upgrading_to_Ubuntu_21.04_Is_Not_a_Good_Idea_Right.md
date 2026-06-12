---
title: "Upgrading to Ubuntu 21.04 Is Not a Good Idea Right Now"
date: 2021-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by C.S.Cameron on 2021-04-29
Anyone know more about this:
[https://uk.pcmag.com/operating-systems/133082/upgrading-to-ubuntu-2104-is-not-a-good-idea-right-now](https://uk.pcmag.com/operating-systems/133082/upgrading-to-ubuntu-2104-is-not-a-good-idea-right-now)

---

### Post by guiverc on 2021-04-29
The bug they mention was in the release notes.

From an answer I wrote on askubuntu ([https://askubuntu.com/questions/1333226/how-can-i-update-to-ubuntu-21-04/1333229#1333229](https://askubuntu.com/questions/1333226/how-can-i-update-to-ubuntu-21-04/1333229#1333229))

> The [release of the ISO has only just occurred]("https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/"); the update from prior releases doesn't get opened until a decision is made on the *stability* of the new release (*watching bug reports* etc) & a decision is made to *turn the taps* (where people are offered the upgrade).  I'd recommend being patient and waiting until you're offered the upgrade.

You can use -d to force... but refer to the [Ubuntu 21.04 Release Notes]("https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221") where you'll note
[INDENT] Upgrades from Ubuntu 20.10 to Ubuntu 21.04 are not enabled as it is  possible for some systems to end up in an unbootable state if they use  EFI version 1.10 - bug [1925010]("https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1925010"). Release upgrades will be enabled once an updated version of shim is available which is compatible with EFI version 1.10.

 [/INDENT]


I don't think it's anything more than that   (*originally reported on apple devices, but also impacts lenovo as I recall & thus likely other brands too, but I haven't watched it*)

---

### Post by coffeecat on 2021-04-29
*Thread moved to **ULOS**.*

This has come up a couple of times in support threads over the last few days:

[https://ubuntuforums.org/showthread.php?t=2461018](https://ubuntuforums.org/showthread.php?t=2461018)

[https://ubuntuforums.org/showthread.php?t=2461152](https://ubuntuforums.org/showthread.php?t=2461152)

---

### Post by lammert-nijhof on 2021-05-10
I had no issues with my Ryzen based desktop upgrading from 20.04 -> 20.10 -> 21.04.

I had problems with a fresh install of Ubuntu 21.04 on my Dec 2011 HP Elitebook 8460p. The BIOS warns, that its UEFI implementation is a prototype, but I have the latest BIOS. I now have to boot the system using the BIOS Boot menu with the UEFI file system entry. If I switch off UEFI support in the BIOS, the system does not recognize the GUID partition table and demands me to install an OS. 

Maybe I should have initialized the new 2TB HDD with the MBR/DOS partition table before installing Ubuntu, but I just moved ~1TB of backups to that new HDD. I'm too lazy to start everything again.

I bought this off-lease laptop in May 2017 during a visit to family in Belgium/Netherlands. Next year I go back for a holidays and I intended to use the same supplier again. At home I use the laptop mainly to backup my desktop once per week, so I will live with this annoyance for 11 months more. 

I'm planning to add an SSD as ZFS cache for the HDD. I'll create a  MBR/DOS partition table on the SSD and maybe I can store the boot loader  there. 

This UEFI/GUID combination has been one of the splendid ideas of Microsoft to harm its competitors, thank you Bill.

---

### Post by grahammechanical on 2021-05-12
This issue seems to have been fixed

[https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10](https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10)

Regards.

---

### Post by jrbassett on 2021-05-17
Personally I am using Ubuntu 21.04 Lubuntu. It works just fine for me.

---

