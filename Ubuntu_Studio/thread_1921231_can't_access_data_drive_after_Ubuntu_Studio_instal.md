---
title: "can't access data drive after Ubuntu Studio install"
date: 2012-02-06
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-02-06
Okay, here is what I did on my dual boot Ubuntu system (Dell Optiplex 330, 4g mem).

(1)  I reinstalled Ubuntu 10 on one partition.

(2)  I removed the ASUS Xonar card from the system, and restored onboard sound in BIOS.

(3)  I reinstalled Ubuntu Studio, and RealTime kernel, using the [instructions on this page.]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

(4)  I assigned both the main user and root to 'AUDIO' group, as per instructions. 

(5)   I tested playback using alsaplayer (OK).

(6)  I tested onboard sound output (OK), and input from the RPx400 (OK) in JACK.

(6)***  I tried to test Hydrogen and Ardour, and ran into a new snag:***

These programs can't access files stored on the other data drive (drumkits, projects etc.).

I investigated and found that although I can access the drive as ROOT, via the Nautilus,
[B]I can't actually read the 'permissions' when I right-click on properties for the drive.
[/B] 
Instead, in the dialog-box (Filesystem/properties/Permissions), I get the following message:
[B][COLOR=Blue]
"The permissions of "soiIOIJElsnesoier" could not be determined."[/COLOR][/B]

I've never seen this before. 
The drive is mounted. 
I am afraid to do anything.
**I don't want to lose 150 Gig of files**.
I DO want to reload drum kits and other files from the drive into Hydrogen and Ardour, as both root and user.

---

### Post by Sylos on 2012-02-06
It may be helpful if you could post the layout of the drives/partitions. Are they partitions of the same drive or different HDDs entirely.

Have you created a mount point for the 'data' drive in /media to allow non root access to it?

Cheers

---

### Post by sgx on 2012-02-06
I would buy another drive and format it with your current system tools,
then copy the 150 meg data from the other drive. then format it with
your system tools, and copy back the data.

You should change the permissions on the files themselves,
so root is not necessary to read/write them

Maybe you could trade the soundcard for a used drive,
and get an mAudio 24/96 pci for recording.
Cheers

---

### Post by nazaroo2 on 2012-02-06
> **sgx said:**
> I would buy another drive and format it with your current system tools,
then copy the 150 meg data from the other drive. then format it with
your system tools, and copy back the data.

You should change the permissions on the files themselves,
so root is not necessary to read/write them

Maybe you could trade the soundcard for a used drive,
and get an mAudio 24/96 pci for recording.
Cheers

I just got an m-audio 24/96.  
I'm going to try it out now.
I traded a copy of Ubuntu 11.10 for it.

---

