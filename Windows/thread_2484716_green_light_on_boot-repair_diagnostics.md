---
title: "green light on boot-repair diagnostics"
date: 2023-03-07
forum: Windows
---

### Post by syntoxr on 2023-03-07
Hi together,
first time here, so I hope this is the right place.

**To my issue:**
Setup:
- I have a Windows 10 pc with two drives:
  - drive1: SSD, 500 GB, with win10 installed on it
  - drive2: HDD, 2 TB, with one partition for storage of data and large files

As drive2 vibrated quite hard recently, I wanted to swap it with a new 2 TB HDD (drive3). So I did the following:
- shut down pc
- plugged in drive3 via SATA
- booted from acronis USB
- cloned drive2 to drive3
- booted successfully to windows
- restarted windows as drive 3 did not get recognized
- bluescreen with CRITICAL_PROCESS_DIED
- windows automatic disk repair with no errors
- failed other windows repair options
- still same bluescreen

So I booted from an Ubuntu USB in order to check if I accidentally chose the wrong drive as a target, but the original partitions and file structure of disc1 seem to be ok.
I've searched a bit around and found boot-repair but was advised to get my diagnostics checked here. ([https://paste.ubuntu.com/p/bzx8D8JShV/](https://paste.ubuntu.com/p/bzx8D8JShV/))

So, here I am kindly asking for your expertise.

Many thanks in advance
Syntoxr

---

### Post by oldfred on 2023-03-07
Moved to Windows sub-forum since not Ubuntu.

You did not show the cloned drive.

Boot-Repair is for fixing Linux systems, it can do very little for Windows systems. Report is useful just to see details of installs. But more for dual boots. 

You may need your Windows repair/recovery flash drive to make Windows repairs. And you may need your backup.

If cloned drive, did you also create duplicate UUIDs as that is not allowed with Linux, not sure how Windows might handle that.

---

