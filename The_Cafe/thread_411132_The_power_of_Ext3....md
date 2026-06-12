---
title: "The power of Ext3..."
date: 2007-04-16
forum: The Cafe
---

### Post by Mazza558 on 2007-04-16
I've been playing with the Windows Ext Partition Drivers and, just for fun, have been installing Windows programs on an empty Ext3 partition. I think, to say the least, the difference in loading speed is incredible when running games/applications on Ext3. 

Here's an article explaining what I did:

[http://mazza558.googlepages.com/home]("http://mazza558.googlepages.com/home")

I've seen for myself that this method seems to be completely safe and reliable, and I'm currently savoring the thought of running all my high-demand games with no snags in terms of loading big textures. It's working fantastically!

Just thought I'd share this with you - tell me what you think!
:)

EDIT: Just found out that it's a bad idea to try this using Vista.

---

### Post by Mazza558 on 2007-04-16
What do you think?

---

### Post by PartisanEntity on 2007-04-16
By how much did it speed up the load times, and does this only affect load times or also the game speed?

What is the technical explanation to this? Anyone know? i.e. why would windows programs run faster Ext3?

---

### Post by Mazza558 on 2007-04-16
Well, the load times seemed quicker because the files never become defrgmented as the main reason. Plus, there's the fact that files running from a different partition open faster because there is less general stuff on a newly created partition. The game speed itself wasn't sped up, but I noticed that there is less pausing to load textures, etc, especially in bigger games.

---

### Post by daynah on 2007-04-16
I thought this was impossible to do :( Like your computer would blow up into a million bunnies or something. Shows what I know.

---

### Post by Mazza558 on 2007-04-16
> **daynah said:**
> I thought this was impossible to do :( Like your computer would blow up into a million bunnies or something. Shows what I know.

Indeed - I was thinking "this cannot be happening...", but it turns out Ext3 works just as good, if not better than NTFS for external applications.

---

### Post by daynah on 2007-04-16
That makes me feel better that I wasn't retardo for thinking that. It must have been the... microsoft propaganda! Dun dun duuun!

---

### Post by BuffaloX on 2007-04-16
Works great,
I actually stopped using fat or ntfs to share files between Linux and XP.
This way all my partitions are ext3, except the XP boot partition.
Well actually my Linux boot is JFS, just to make sure Windows malware doesn't mess it up.:-& 

If you use Daemon tools, disable automount of virtual CDs on ext3, because
ext3 apparently is loading after Daemon tools.
The result is of course a total XP crash, which is the only logic reaction for Windows to that kind of problems.

PS
Does anybody know how to load the ext2 driver at an earlier point of the boot process of XP?
so I can auto mount again.

---

### Post by Mazza558 on 2007-04-16
> **BuffaloX said:**
> Works great,
I actually stopped using fat or ntfs to share files between Linux and XP.
This way all my partitions are ext3, except the XP boot partition.
Well actually my Linux boot is JFS, just to make sure Windows malware doesn't mess it up.:-& 

If you use Daemon tools, disable automount of virtual CDs on ext3, because
ext3 apparently is loading after Daemon tools.
The result is of course a total XP crash, which is the only logic reaction for Windows to that kind of problems.

PS
Does anybody know how to load the ext2 driver at an earlier point of the boot process of XP?
so I can auto mount again.

I don't think there is any free way to do that, but there are several commercial products that allow you to order the programs at boot.


EDIT:

I have more proof of fast-loading games! I posted this on some forums (Guild Wars) and someone tried it out:

> **eggrolls said:**
> Just tried it out. Took less than 10 minutes since I happen to have a Ubuntu CD nearby.

I have two hard drives, one SATA and one IDE. The IDE hard drive has both NTFS and the new EXT3 partitions. I copied the GW folder over to the EXT3 partition. It seemed to take forever. I then restarted my computer to begin testing.

I loaded GW and timed how long it took from pressing enter on the icon to the login screen:
SATA (NTFS): ~10 seconds
(Restarted computer again to keep it equal somewhat...)
IDE (EXT3): ~5 seconds

Certainly a noticeable increase in load times. I then restarted my computer again to test file copying (GW.dat, ~4GB):

SATA to IDE (minutes:seconds)
NTFS to NTFS = 2:02
NTFS to EXT3 = 2:54

IDE to SATA
NTFS to NTFS = 1:58
EXT3 to NTFS = 2:42

Copying files to and from an EXT3 partition is about 40% slower. Well, at least GW loaded nearly twice as fast. That's what matters right? lol

---

### Post by Mazza558 on 2007-04-17
Anyone else got any thoughts?

---

### Post by Bloodfen Razormaw on 2007-04-17
> Well, the load times seemed quicker because the files never become defrgmented as the main reason.
Ext3 does get fragmented.  In fact, while it usually doesn't get fragmented badly, in its worst case the fragmentation can be far more severe than anything you will ever see on an NTFS filesystem.

---

### Post by dreadlord_chris on 2007-04-17
Interesting.... just keep in mind Windows security permissions will not get applied to ext3 filesystem objects.

---

### Post by FoolsGold on 2007-04-17
> **Bloodfen Razormaw said:**
> Ext3 does get fragmented.  In fact, while it usually doesn't get fragmented badly, in its worst case the fragmentation can be far more severe than anything you will ever see on an NTFS filesystem.
I've heard though (never bothered to check) that a heavily fragmented Ext3 partition will eventually clean itself up after regular use, so long as there's a healthy amount of free space available. You don't even have to do anything yourself, regular use will facilitate its recovery.

---

### Post by Polygon on 2007-04-17
the thing is, that driver for windows is for ext2 partitons. which means... if you format the partition as ext3 on like ubuntu, and then access it from both ubuntu and windows, then its going to get a bit screwed up

cause ext2 is basically ext3, only without the journal. So, from my own experiences from using the ext2 driver for windows, ubuntu complained alot about the drive in question that was being used by windows via the ext2 driver that it was failing its drive test and i needed to run fsck on it

my question is, why dont they just make a driver that works with ext3?

and anyway, interesting results.

---

