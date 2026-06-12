---
title: "Installing on a RAID 1"
date: 2007-11-30
forum: Server Platforms
---

### Post by vsiege on 2007-11-30
I am running into trouble... and now im stuck.

I set up a RAID 1 using the BIOS (Intel ICH8R Southbridge RAID Controller). That worked.
Then I installed U.S. 7.10

When in the installer it came down to partioning I choose the first option to guided partition, then selected the SATA 1 (it saw two drives instead of one) when asked to choose a disk - was this right?

The installation app said it was Complete and to restart.
Without the CD in the DVD drive I get to this message:
[INDENT]Reboot and Select proper Boot device or insert boot media device and press a ket[/INDENT]I pressed a button jjust to see and got **GRUB**
but nothing happened

What im looking to have is a server that mirrors info to a second drive - is RAID 1 not the best way?
[INDENT]MOBO: P5K-E / 2 seagate 500 / 4 ghz RAM / IDE DVD-RAM and no other drives or speacial cards[/INDENT]

---

### Post by bnuytten on 2007-12-15
You should defintly read about the[ "fakeraid" howt]("https://help.ubuntu.com/community/FakeRaidHowto")o. I have Gutsy running on both software RAID (mdadm) and fakeraid, one RAID0 and one RAID1.

---

