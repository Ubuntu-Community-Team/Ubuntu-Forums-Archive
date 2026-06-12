---
title: "Possible linux virus on the loose ?? A short horror story"
date: 2006-06-30
forum: Server Platforms
---

### Post by Dogmeat on 2006-06-30
Ok this may sound a bit crazy, but I was using my computer as always, then suddently the computer seemed half-frozen, as in, it would update but it would not respond.

It was not a usual freeze, I could do console switching and I saw my enters working, but the system would not respond. The only option was a reboot.

Grub apparently was working as normal. Suddently, it said something about the CPU not being in sync, then kernel panic. Another reboot. This time grub would hang. Other times Ubuntu would load half the way, etc. But it never booted fully, even after a live cd and a  hard reset (I pulled the plug literally).

BUT WAIT! I know many of you are thinking "Some noob sees his drive die for the first time and thinks its a virus. Next thread."

Please wait. While I saw other drives die, I never saw something like this, so I could use some honest opinions from experienced folks.

I read about a guy saying one of his Maxtor drives only works upside down and I found it funny at first, so I sai I have a dead drive here so what do I have to lose. And I tried it. After pulling it from the case and turning it upside down, nothing happened. I slapped it around a bit with a large trout (kidding.. I just shook it a bit :P)
and VOILA! parted could read the partitions again!

I was a bit relieved, because I thought my hard drive was dead. It was clicking loudly before. After doing this, I haven't heard a single click in more than 24 hours.

I proceeded to back up my 7 partitions to various places on the network with ddrescue, as I was afraid of losing data. However as I recently found, the damage was done. But in a very strange way, look at this badblocks file I got after moving the data:

```

0
1
32760
32769
98296
98304
98305
163832
163840
163841
229368
229376
229377
294904
294912
294913
819192
819200
819201
884728
884736
884737

```

This is from the first partition, the only one that got trashed and whose filesystem is now unrecognized by parted.
If you look closely, the bad blocks are exactly near the boot sector and in EACH AND EVERY ONE of the redundant superblock inodes (the blocksize was 4096 bytes). So, one of these should be true:

1) Is it normal for a drive to selectively kill all the superblock inodes and the boot sector, while leaving the other dozens of gigabytes intact? I sincerely doubt it, so I posted this.

2) I was simply extremely unlucky? (Doubtful too)

3) A new type of linux virus on the loose? (While difficult, if you consider the thousands of packages you have installed, it is possible an unscrupulous person snuck a virus in there)

I'm really curious as why this would happen. Please enlighten me. Also, how big are the superblocks on a 10 GB partition? Maybe I can manually reconstruct the superblock with dd with the good surrounding blocks?

---

### Post by Wr8EYilK8Y on 2006-06-30
PCWorld did say something about a "POT" virues- Possibility of Theory, IIRC- it infects Windows XP based AND Linux 2.6 machines. Very nasty stuff. I would not know beyond this- but I do have 3 separate OS each with its own partition, Antivirus, and Firewall for doubled security. You get the idea.

I would be very suspicious if I were you.

---

### Post by Dogmeat on 2006-07-01
Well I do have a firewall running in deny by default mode (both ways), but no antivirus.

This is why I'm especially suspicious of some random package (open source or proprietary) I may have installed. I'll see if I can flash my hard drive, if the damage was caused by a virus (in other words, not physical) the badblocks should be gone, correct? I'm at the moment doing trying some surgery on the broken partition's copy. I'll keep updating this thread if I find something interesting.

Meanwhile, if you can dig up that POT virus link I woul d be grateful, a quick googling found nothing about it. By the way, was it in any way connected to rar files? I was extracting a rar file when all of this happened.

---

### Post by MJN on 2006-07-01
What's the SMART status of your drive? Have you run an extended test on it? Any previous error in the logs?

---

### Post by Lord Illidan on 2006-07-01
I doubt it was a virus in the packages. They are checked quite well, and thus it would be almost impossible to slip a virus inside.

In fact, I think it was more due to hardware problems. Your harddisk was going to die, and it did. No virus.

---

### Post by Dogmeat on 2006-07-01
[QUOTE=MJN]What's the SMART status of your drive? Have you run an extended test on it? Any previous error in the logs?[/QUOTE]

I just installed smartmontools in my intact 64-bit Ubuntu partition (only the first partition got bad blocks). I went in the BIOS and enabled SMART monitoring for the drive. However I got this from running smartd -q onecheck:

```

smartd version 5.36 [x86_64-redhat-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Opened configuration file /etc/smartd.conf
Drive: DEVICESCAN, implied '-a' Directive on line 23 of file /etc/smartd.conf
Configuration file /etc/smartd.conf was parsed, found DEVICESCAN, scanning devices
glob(3) found no matches for pattern /dev/sd[a-z]
glob(3) aborted matching pattern /dev/discs/disc*
Problem creating device name scan list
Device: /dev/hda, opened
Device: /dev/hda, not ATA, no IDENTIFY DEVICE Structure
Unable to register ATA device /dev/hda at line 23 of file /etc/smartd.conf
Device: /dev/hdc, opened
Device: /dev/hdc, not ATA, no IDENTIFY DEVICE Structure
Unable to register ATA device /dev/hdc at line 23 of file /etc/smartd.conf
Unable to monitor any SMART enabled devices. Try debug (-d) option. Exiting...

```

It should detect hda as ATA but it doesnt. I used the smartmontools for 64-bit RPM, alien'd it to a DEB and installed. Running with the -d option gives me the same output.

[QUOTE=Lord Illidan]I doubt it was a virus in the packages. They are checked quite well, and thus it would be almost impossible to slip a virus inside.[/QUOTE]

Ok, let's say it didn't come from the packages. Most of us probably download non-free and other files which could be infected. That's not the point, I just found it really strange to have the boot sector, and every redudant superblock of the first partition damaged.

My other partitions are fine, so this looks like some sort of targeted attack. Now SMART doesn't work. Unfortunately I could not find a firmware upgrade to my drive yet. That would find out for sure if it was a virus or not.

---

### Post by RavenOfOdin on 2006-07-01
[QUOTE=Dogmeat]
I read about a guy saying one of his Maxtor drives only works upside down and I found it funny at first, so I sai I have a dead drive here so what do I have to lose. And I tried it. After pulling it from the case and turning it upside down, nothing happened. I slapped it around a bit with a large trout (kidding.. I just shook it a bit :P)
and VOILA! parted could read the partitions again!
[/QUOTE]

This does sound like a hardware problem.  
A virus - no matter what platform/OS - shouldn't respond to the HD being shaken.  If it did, there'd be a whole new AV market out there. 

Maybe some of the connectors on the back end didn't touch where they needed to.

So. . .Yeah.  I'll have to echo Lord Illidan's previous post. You just need a new hard drive.

---

### Post by Wr8EYilK8Y on 2006-07-01
I can't find the POT thing- but you should be able to look it up at [www.pcworld.com](www.pcworld.com) with their search button

---

### Post by MJN on 2006-07-02
Dogmeat, please don't take this the wrong way but it sounds to me like your knowledge in this matter is insufficient to confidently conclude a viral cause or not.
 
Your excitement is understandable - there's nothing more boring than (semingly) random failures, particularly hardware-based ones, that affect us all from time to time.
 
Mathew

---

### Post by Wr8EYilK8Y on 2006-07-04
My video hardware doesn't always work on boot-up. Sometimes, I get the two-beep error code for failure to start video device. Virus? I think not. I just restart.

---

### Post by simonn on 2006-07-04
[http://en.wikipedia.org/wiki/Occams_razor](http://en.wikipedia.org/wiki/Occams_razor)

---

