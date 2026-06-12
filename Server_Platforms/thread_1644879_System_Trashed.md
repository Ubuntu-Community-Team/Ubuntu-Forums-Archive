---
title: "System Trashed"
date: 2010-12-13
forum: Server Platforms
---

### Post by Vegan on 2010-12-13
Yesterday my Linux machine crapped out. On review it came up with the GRUB menu and no matter which kernal, they all failed and the system came up in single user mode.

Booting a Live Desktop CD showed that the file system was completely thrashed.

No problem as I have daily backups, but this is not the fist time this has happened. 

I have tested the hardware ad nauseum and its fine. So this leaves dodgy software at issue.

Anyone else experience crashed file systems and partitions etc?

---

### Post by garryconn on 2010-12-13
Not sure what the problem is, but one thing that could help you is to create a /home partition on your drive during install. That way when you do have future problems with your system you don't have to worry too much with the backups. When you reinstall the OS, everything in your /home partition will already be there ready to go.

---

### Post by arrrghhh on 2010-12-13
Was there a recent update...?  Usually things don't just blow up for no reason, short of hardware failure which you said you have ruled out...

---

### Post by Vegan on 2010-12-13
I use tar and gzip and mysqldump and save everything to a dedicated path that is shared with SAMBA.

Its all done with a shell script

I use a Windows shell script to copy the files from the SAMBA path to a secondary drive used for backups and my MP3 collection.

I have my machine set for automatic updates as I assume Linux is under the same level of malware attacks as Windows. I see tons of attempts to break in to my server but my server is very secure with a hardware firewall via my Linksys WRT54GL

I wonder if one of the recent updates was at fault?

I have automatic updates on

---

### Post by Vegan on 2010-12-13
I should also point out the installer does not even see any partitions when I reinstall.

Seems the table is wiped out

---

### Post by CharlesA on 2010-12-13
Woah. That's not good at all.

How do you have the updates set up? To do all of them automatically, and reboot as needed?

Does the installer see any drives at all?

The only time I've had my file system get totally borked is after a sudden power outage, or if the machine rebooted unexpectedly (bad RAM), which was fixed by running fsck from a livecd.

That being said, I haven't run into that lately, thankfully.

---

### Post by arrrghhh on 2010-12-14
> **Vegan said:**
> I have my machine set for automatic updates as I assume **Linux is under the same level of malware attacks as Windows**. I see tons of attempts to break in to my server but my server is very secure with a hardware firewall via my Linksys WRT54GL

I would say no, this isn't true - now that doesn't mean you should ignore security updates, and automatic security updates should be fine.

I'm curious as well - how do you do your automatic updates...?  I can think of two ways, and one of them could possibly cause issues... I would hope not this drastic of an issue, but perhaps if the incorrect option was selected...

---

### Post by rubylaser on 2010-12-14
Short of either a hardware problem (ram, or more likely hard drive) the only thing that would wipe out the partition tables is fdisking or dding the drive.  These last two don't run on their own, so it sounds like a bad hard drive to me.  Although, you said the hardware's been tested, have you ran smartmontools and badblocks on the drive?

---

