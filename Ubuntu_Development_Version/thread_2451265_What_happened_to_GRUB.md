---
title: "What happened to GRUB ?"
date: 2020-09-30
forum: Ubuntu Development Version
---

### Post by cr6 on 2020-09-30
Hi there! ):P

Today I wanted to test Xubuntu 20.10 "Groovy Gorilla".

I downloaded the latest ISO here:
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/groovy-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/groovy-desktop-amd64.iso)

I tried to install it on my HP laptop (an 11-year-old machine BIOS/MBR), but something went wrong with GRUB.

1) Right from the start I noticed a difference between 20.04 and 20.10 (see my first two screenshots)

2) During the installation process I got a serious problem related to EFI and I was unable to complete the installation (see my other three screenshots)


Thanks for your help

---

### Post by CelticWarrior on 2020-09-30
Welcome.

Your machine is actually UEFI and you booted in UEFI mode (the Grub menu in the second screenshot is typical of UEFI) and then it installs in UEFI mode but can't because there isn't the required EFI partition. It's all perfectly clear.

It's a good thing you noticed. If the machine is UEFI then install in UEFI mode, it's simple. But, of course, do your backups first and then install from scratch without reusing the previous partitions. And another thing: A swap partition is no longer needed. Ubuntu uses a swapfile by default now.

---

### Post by cr6 on 2020-09-30
> **CelticWarrior said:**
> Welcome.

Your machine is actually UEFI and you booted in UEFI mode ... 

No, my machine is not UEFI, it's BIOS/MBR. Moreover, the issue does not occur with Xubuntu 20.04, neither in Debian/Devuan ... :confused: :cry:

---

### Post by sudodus on 2020-09-30
The boot structure has changed a lot in Groovy.

1. Booting a live drive from USB

 The syslinux boot in BIOS mode is replaced by grub and the grub boot in UEFI mode is modified, so that some computers that boot in 20.04.x LTS no longer boot. There is a [bug report](http://launchpad.net/bugs/1886148) about that, and it is improved now for most computers, but not all of them. For example, some rather new Lenovos have problems.

2. Installing and booting the installed system

But I think you have another problem, that is related to installing and/or booting the installed system. There are current bug reports about that too, but I am not sure if your problem is described by any of those.

Anyway, have a look at [this bug report](http://launchpad.net/bugs/1893964), that might be it.

---

### Post by cr6 on 2020-09-30
[https://ubuntuforums.org/showthread.php?t=2448089](https://ubuntuforums.org/showthread.php?t=2448089)

---

### Post by howefield on 2020-09-30
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by sudodus on 2020-09-30
So it seems that the installer wants to create an EFI system partition (at least in VirtualBox, maybe also in a real computer) even when you intend to boot in BIOS mode. Interesting :-/

---

### Post by este.el.paz on 2020-09-30
I'll drop my comments/situation in this thread . . . I and others have been experiencing problems with ubuntu's adjustments to grub for quite awhile, pre-dating groovy, but continuing on in it as well.  In my case, this morning, again for the umpteenth time, running some apt upgrades in one of my three ubuntu based distros . . . the grub listings were wiped and the computer will only boot into either U-MATE or now the last installed distro, which is LM 20.04 . . . "focal" based . . . same problem.

I have tried to just run updates via Software Updater to uncheck anything that has "GRUB" listed in it, because each of the updates to anything "grub" again wipe out the connections to my other 3 or 4 distros . . . and I have to use SG2 disk to boot into TW and then run their "mkconfig" command to restore functional grub.  This morning since grub had been wiped I ran LM's apt dist-upgrade, let it run through what was mostly the "grub" packages . . . it showed the "dpkg"??? of finding the other linux distros, so it can "see" them . . . but, on reboot . . . nada . . . I ran "update-grub" as well . . . no dice.

In my case it is an EFI computer, and on install I flag the EFI partition for grub . . . but something about ubuntu's "grub" doesn't seem to "work" with EFI???  This is my seat o the pants diagnosis . . . .  Over possibly the last year I have filed a number of bug reports . . . devs on one were like, "That's the way it's supposed to be . . . " ????  I said, ubuntu wants grub to erase all other listings, is that what you are saying???"   No reply to that query . . . .

My latest bug report on the topic of "What the heck happened to GRUB?"   Grub appears to be MIA or only works for ubuntu flavorings????   

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1894242](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1894242)

---

### Post by cr6 on 2020-10-07
Well, the should've called it "**Goofy Gorilla**" ... =d>

That's really sad. :(

Okay, I give up.

---

### Post by oldfred on 2020-10-07
It has always been one /EFI/ubuntu folder in ESP and one ubuntu entry in UEFI.
And then from grub menu, you can boot other installs.
Last install of Ubuntu (or flavor or other distributions that use Ubuntu) will be the one in control.

See this bug from 2015:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783)
I tried changing distributor in my Ubuntu and it then does create a new /EFI/entry, but something is hard coded to only use /EFI/ubuntu/grub.cfg as configfile into your install (last install). I have had to edit that grub back to my main working install when making a test install that I do not want as default boot.

I now do this will all my second installs, but still only have one UEFI boot entry. I turn off os-prober and add entries to 40_custom.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by cr6 on 2020-10-07
@oldfred  I feel like you take me for an idiot ... :roll:

Okay, let's tell the truth: I'm a former Void linux developer & forum moderator, so I'm not a beginner ...

Groovy Gorilla is just ***broken*** on some computers, that's it.

Have a good night.

---

### Post by cr6 on 2020-10-07
...

---

### Post by cr6 on 2020-10-07
> **oldfred said:**
> change to [Solved] when/if answered completely.[COLOR=Navy]
[/COLOR]

Still broken. :(

---

### Post by saivinoba2 on 2020-10-16
> **sudodus said:**
> So it seems that the installer wants to create an EFI system partition (at least in VirtualBox, maybe also in a real computer) even when you intend to boot in BIOS mode. Interesting :-/

I tested several scenarios today and following are my observations.

1) Groovy ISOs now default to GPT partitioning scheme by default (for erase and install). 
   a) If we booted in BIOS mode, this will create minimum three partitions, 1M 'BIOS grub', 512M as 'EFI System Partition' for /boot/efi and remaining for /.
   b) If we booted in UEFI mode, this will create two partitions, 512M as 'EFI System Partition' for /boot/efi and remaining for /
   c) If we are doing manual partitioning, it is not mandatory to create a BIOS grub partition. Just and EFI partition and root partition is sufficient.

2) Focal ISOs default to MBR partitioning if booted in BIOS mode and GPT if booted in UEFI mode. However, I noticed, for BIOS mode, Focal will offer following partitioning scheme,
   a) during install but before grub-install: 512M as W95 FAT32 (/dev/sda1) and remaining for / (/dev/sda5, extended partition)
   b) after grub-install: 512M /dev/sda1 will change time to ef (EFI FAT 16/24/32). It will be mounted as /boot/efi (or /target/boot/efi during install).

@cr6,
Please create an EFI partition (200M should be enough, no formatting required) when you want to install.

---

### Post by Morbius1 on 2020-10-17
It appears they have given up trying to fix this for 20.10: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964)

The last post - at this moment:
> Given that there is a warning presented for this situation we've decided to same this for fixing in the HH release of Ubuntu.

The "HH" reference is to the next release - 21.04.

---

### Post by zacktu on 2020-11-12
I thlnk that the result of this is that my attempt to install GG to replace an installation of FF in a dual-boot environment with another FF on a Lenovo laptop with a /boot partition just won't work.  Is that right?

---

