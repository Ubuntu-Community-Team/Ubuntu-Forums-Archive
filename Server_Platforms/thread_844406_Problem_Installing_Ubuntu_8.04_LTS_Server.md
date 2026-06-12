---
title: "Problem Installing Ubuntu 8.04 LTS Server"
date: 2008-06-29
forum: Server Platforms
---

### Post by kadafi69 on 2008-06-29
Ive just tried setting up my first server, and ive instantly hit a wall.

popped in the live CD, all worked fine, ejected the disk and rebooted, im not greeted with this error.

> Searching for Boot Record from IDE-0..OK
Boot Failure from Previous Device..
Searching for Boot Record from BBS-1:[Intel UNDI, PXE-2.0 (build 082)  ]...OK

Intel UNDI, PXE-2.0 (build 082)
Copyright © 1997,1998,1999 Intel Corp
VIA Rhine II Fast Ethernet Adapter						v2.13  (2002/08/09)

PXE-MOF: Exiting Intel PXE ROM.
Boot Failure from Previous Device..
Searching for Boot Record from SCSI..Not Found

Boot Failure
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device
Press any key when ready


i take it this has something to do with the PCI sata card i have installed on the machine?!?

anyone know how to turn things around?

---

### Post by mrpeenut24 on 2008-06-29
It's running through your devices trying to find a bootable medium.  Did you see a grub menu by chance?  If not, then it's not set up properly and can't boot from the hard drive.  The sata card *shouldn't* matter, I don't think.

---

### Post by kadafi69 on 2008-06-29
no there was no grub, so i take it theres a problem with the installation. ill give it another go and see what happens.

---

### Post by windependence on 2008-06-30
Yes, the SATA card changed the boot order. remove the card and reboot and if it works then the card is the reason. You can fix it by messing with the grub menu, but actually you should have done the installation prior to adding the card.

-Tim

---

### Post by satimis on 2008-06-30
Hi,


I don't have exact solution.  I can give you some hint.  In the past I did installing OS, Linxu and Windows, many times on HD connected to ATA card.  The card must be detected automatically by the motherboard before the OS starts to boot.  A driver comes togther with the ATA card.  


I suppose it will be the same on SATA card.


B.R.
satimis

---

### Post by kadafi69 on 2008-06-30
ok, it was the sata card that was causing the problems, removed it and then re-installed, worked fine. need to find a way to make it work now!

---

### Post by kadafi69 on 2008-06-30
im now having a problem trying to update. Im getting this error

> Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.9p9.gpg
Could not resolve .gb.archive.ubuntu.com.

Reading package lists... Done

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)
Could not resolve .gb.archive.ubuntu.com.

W: Some index files failed to download, they have been ignored, or old ones used instead.
W:You may want to run apt-get update to correct these problems

There is a massive list of errors for each repo.

---

