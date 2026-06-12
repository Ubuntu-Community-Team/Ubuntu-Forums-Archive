---
title: "Raid 5 on Poweredge 1425"
date: 2006-03-27
forum: Server Platforms
---

### Post by wylie348 on 2006-03-27
Just did an install of Ubuntu 5.10 with this system, and used the raid 5 setup for three 73 GB drives using the sata card bios setup.  Install recognized the 'drive' correctly as approx 148 GB, but I have two concerns:

1)  how do I monitor the status of the RAID array from ubuntu (rather than just seeing the 148 GB drive)

2) does the RAID card (cerc sata) actually handle all of the mirroring of the data without something requiring to be set in the OS? - in other words all of the striping (with parity)...

Thanks for any advice.  It all appears to be working but I would hate for it not to be reliable...
:D

---

### Post by zac1333 on 2006-03-27
I'll give this a whirl, since I have some experience with Dell PowerEdge's

1) I'm not sure of any way to monitor the status of the RAID array from Ubuntu.  Is there something in particular that you wanted to monitor?  Normally, if anything is wrong, your PowerEdge will start beeping and there will be an orange light on the drive with an issue.

2) The RAID card handles all of the functions.  Ubuntu passes the data to the RAID card, and the RAID card takes care of putting the data where it needs to go and whatnot.  That's the nice thing about a hardware based RAID array - the card does all that for you, without eating up your cpu usage like a software based RAID array would.

I hope this helps.

---

