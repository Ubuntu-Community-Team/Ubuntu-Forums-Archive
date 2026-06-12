---
title: "What do people think is the best backup software?"
date: 2015-11-10
forum: Ubuntu, Linux and OS Chat
---

### Post by UncleMonty on 2015-11-10
I currently use GRSYNC, but even with usb 3.0 it's still slower than a three legged tortoise. What do other people use? Are there any better options?

---

### Post by Mark Phelps on 2015-11-10
I've used Clonezilla: old-fashioned interface, little difficult to master, but works well and fast.  Less than 5 minutes to do an image backup.  Website has instructions for adding boot information to GRUB stanzas so you don't have to mess around with booting CD or USB.

---

### Post by pretty_whistle on 2015-11-10
I use Re-do backup.  I find it easier to understand than Clonezilla.

---

### Post by Bucky Ball on 2015-11-10
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Clonezilla to back up partitions now and then, Luckybackup (in the repositories) once or twice a week. [This question has been asked many times previously]("http://ubuntuforums.org/search.php?searchid=9404522") so don't be too surprised if another staff member decides to further move this on to ***Recurring Discussions***. :)

Good luck in your search.

---

### Post by Old_Grey_Wolf on 2015-11-11
There are a few questions that you need to think about when choosing backup software.

Is your backup disk at least as large as the partition you what to backup? If not, that can rule out some backup/clone software.
Do you need your backup encrypted? That can effect the speed of some backup solutions to some extent.
Do you want to backup /home or do you need to backup more than that?
Do you need to backup all files every time or just the ones that have changed since the last backup? That can really slow down the backup speed if it is backup all files every time.

---

### Post by sammiev on 2015-11-11
> **Mark Phelps said:**
> I've used Clonezilla: old-fashioned interface, little difficult to master, but works well and fast.  Less than 5 minutes to do an image backup.  Website has instructions for adding boot information to GRUB stanzas so you don't have to mess around with booting CD or USB.

+1

and since I use a USB backup drive, the room is plentiful.

Can restore Windows and 2 or 3 Linux OS in less than 30 mins.

---

### Post by Habitual on 2015-11-11
+1 rsync + USB < 30m.

---

### Post by mikodo on 2015-11-11
> **Old_Grey_Wolf said:**
> There are a few questions that you need to think about when choosing backup software.

**Do you need to backup all files every time or just the ones that have changed since the last backup? That can really slow down the backup speed if it is backup all files every time.**
+1 To all questions.

If you want a backup software that provides for all files and their changes, this is a fast "incremental" solution: [URL="http://rdiff-backup.nongnu.org/"]rdiff-backup 
[/URL]

---

### Post by robboguy on 2015-11-12
CrashPlan works good for me

---

### Post by bruakerche on 2015-11-13
I only back up user and code files via a USB stick, lol. Am I dumb? When refer to phone backup, [COLOR=#ff0000]Titanium[/COLOR] is my favorite option for full backup and this [app]("http://www.androidphonesoft.com/resources/copy-sms-from-samsung-to-computer.html") for partial backup.

---

### Post by fjgaude on 2015-11-13
> **UncleMonty said:**
> I currently use GRSYNC, but even with usb 3.0 it's still slower than a three legged tortoise. What do other people use? Are there any better options?

I've used grsync for years for near and far lines. Its speed is controlled by the source and destination speeds. Why would it not be? Of course, the LAN and WAN speeds could be a bottleneck.

---

