---
title: "Unable to boot from HDD 20.04 installed with BIOS in Legacy mode"
date: 2020-12-10
forum: Server Platforms
---

### Post by mdlueck on 2020-12-10
Greetings,

I suspect there might be a defect in Ubuntu Server 20.04 ISO. I was loading it onto a ThinkPad to test out the new Ubuntu Server LTS release. I had the ThinkPad BIOS set to boot from legacy mode disks, all UEFI disabled.

The partitions Ubuntu Server 20.04 created for me were as follows:

Disklabel Type: gpt
sda1 BIOS Boot
sda2 Linux filesystem (which I selected xfs)

The system failed to boot from the HDD. When trying to boot from the system's HDD, I only am able to get the ThinkPad "Boot Menu / Application Menu" screen to come up. Selecting ATA HDD0 loops back around to the same menu.

It was suggested that Ubuntu 20.04 really prefers to boot from drives in UEFI mode. I changes the BIOS settings, wiped the disk during another test installation. This time the partitions the installer created were as follows:

Disklabel Type: gpt
sda1 EFI System
sda2 Linux filesystem (which I selected xfs)

And the system does boot from the HDD now.

So is this a defect in the installer for Ubuntu Server 20.04 that it does not produce a bootable drive when the computer BIOS is set to legacy boot mode?

I was expecting to see the legacy boot partition table type not be a gpt partition table. Might that have something to do with the failure to boot?

I think the fact that for the legacy boot installation, Ubuntu Server did at least create a first partition of type "BIOS boot".

Suggestions?

I am thankful,

---

### Post by mdlueck on 2021-01-18
Greetings,

I tried the same installation on the same ThinkPad from the ubuntu-**20.04.1**-live-server-amd64.iso disk. Same results as before.

Looks like Ubuntu Server has a defect booting from disks where the BIOS is set to legacy mode.

This is not broken in Xubuntu 20.04 installation.

Logging an Ubuntu Server installer defect.

"Ubuntu Server 20.04 installation to drive with BIOS set to legacy mode results in non-booting drive"
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1912276](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1912276)

I am thankful,

---

### Post by darkod on 2021-01-18
Have you tried the legacy ISO?

Personally, as long as the "old type" ISO exists I try to stay away from the -live-server- image. I still haven't reinstalled my server so I have no test done on 20.04.

FYI legacy image is here:
[http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04.1/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04.1/release/)

---

### Post by guiverc on 2021-01-19
Most desktop releases use `ubiquity` (modern Lubuntu, the last Ubuntu Studio release do use `calamares` as it's easier with Qt based systems), but they are different installers to the server systems.

The traditional (legacy) installer for servers was the Debian Installer (text based; also used by Lubuntu up to 18.04 as it allowed installations where the PC had 768MB or less of RAM; which wasn't enough to run a *live* system and the installer at the same time; but this was dropped after 18.04).

Modern Ubuntu Server installations use `subiquity`, which is the "live" server installer. It's only a semi-recent thing, and has improved ([https://ubuntu.com/blog/updatable-ubuntu-server-live-installer](https://ubuntu.com/blog/updatable-ubuntu-server-live-installer)), once it handles everything, the Debian Installer image will be dropped for Ubuntu Server.

Your bug report is filed, is on the desktop installer though (not the *live* server installer).  I was tempted to change it, but unless there is a reason why you filed against the desktop installer, I'd suggest you changing it, then running the requested `apport-collect` on your system so full details can be made available on the bug report.

Subiquity has been improving with each release - it's still new software.

Thank you for helping make Ubuntu better :)

---

### Post by mdlueck on 2021-01-19
> **guiverc said:**
> Your bug report is filed, is on the desktop installer though (not the *live* server installer).  I was tempted to change it, but unless there is a reason why you filed against the desktop installer, I'd suggest you changing it, then running the requested `apport-collect` on your system so full details can be made available on the bug report.

Subiquity has been improving with each release - it's still new software.

Thank you for helping make Ubuntu better :)

Greetings guiverc,

I find it very difficult to find the name of the Ubuntu installer package at all in the long list of packages. 

When I end up with a non-booting system, it makes it quite challenging to run `apport-collect` on the system. I have done so now.

I am thankful,

---

### Post by darkod on 2021-01-20
Out of interest, did you manage to achieve this with the legacy image?

---

