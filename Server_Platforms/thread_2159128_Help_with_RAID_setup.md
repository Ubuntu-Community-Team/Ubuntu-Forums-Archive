---
title: "Help with RAID setup"
date: 2013-07-01
forum: Server Platforms
---

### Post by nerdtron on 2013-07-01
Hi all,

I have an LSI MegaRAID controller and 12 HDDs that I want to setup for RAID 6.
I'm not familiar on how to group the drives, is it 4 volume groups with 3 HDD each, or 3 volume groups with 4 HDD each? Not to mention 2x6 or 6x2 combinations. Or just one big volume group?

I'm familiar with RAID 10 setups, I configure it with 2 volume groups and 6 drives each. But how do I group the drives for RAID 6?

Thanks!

---

### Post by CharlesA on 2013-07-01
Are you wanting to do one big RAID6 array or smaller RAID6 arrays?

If you are going to use it like one huge disk, just add the drives to the array and you'll be good to go. The OS should see it as xx TB in size.

---

### Post by nerdtron on 2013-07-01
That's what I'm not sure about, is it better to use one large disk or smaller arrays? We are going to use it for File Storage with NAS4Free as the OS.

Will smaller arrays still work if two drives fail?

---

### Post by CharlesA on 2013-07-01
I dunno. I've always done one huge array. With RAID6, you'll be protected from 2 drive failures, so I'd go with a 12 disk RAID 6 array and see what happens. ;)

---

### Post by nerdtron on 2013-07-01
Alright then, I'll go with one large array. Thanks :D

---

### Post by CharlesA on 2013-07-01
Welcome. :)

Let me know how you go about creating it cuz I'm going to be migrating my current RAID card to MegaRAID and have no idea what I'm doing. :lolflag:

---

### Post by rubylaser on 2013-07-02
NAS4Free's default filesystem is ZFS.  With ZFS, hardware RAID controllers are about the last thing you want to use.  It prevents ZFS from giving you almost all of it's good benefits.  All you really need is a "dumb" HBA like the IBM m1015 or LSI 9211-8i in IT mode to hang your disks off of.  For a simple fileserver, I would suggest one large RAID6 array (or raidz2 in ZFS speak).

---

### Post by rubylaser on 2013-07-02
> **CharlesA said:**
> Welcome. :)

Let me know how you go about creating it cuz I'm going to be migrating my current RAID card to MegaRAID and have no idea what I'm doing. :lolflag:

I know someone you could ask if you have any questions :)

---

### Post by CharlesA on 2013-07-02
> **rubylaser said:**
> NAS4Free's default filesystem is ZFS.  With ZFS, hardware RAID controllers are about the last thing you want to use.  It prevents ZFS from giving you almost all of it's good benefits.  All you really need is a "dumb" HBA like the IBM m1015 or LSI 9211-8i in IT mode to hang your disks off of.  For a simple fileserver, I would suggest one large RAID6 array (or raidz2 in ZFS speak).

I had no idea a file system would negate the benefit of using a hardware RAID card. *goes off to google*

> **rubylaser said:**
> I know someone you could ask if you have any questions :)

Lol. This is true. ;)

---

### Post by rubylaser on 2013-07-02
> **CharlesA said:**
> I had no idea a file system would negate the benefit of using a hardware RAID card. *goes off to google*

The filesystem doesn't negate the benefit of hardware RAID.  In the case of ZFS, the hardware RAID card prevents some ZFS's features from working.  Here are a few from [Wikipedia]("https://en.wikipedia.org/wiki/ZFS#ZFS_and_hardware_RAID").

---

### Post by CharlesA on 2013-07-02
> **rubylaser said:**
> The filesystem doesn't negate the benefit of hardware RAID.  In the case of ZFS, the hardware RAID card prevents some ZFS's features from working.  Here are a few from [Wikipedia]("https://en.wikipedia.org/wiki/ZFS#ZFS_and_hardware_RAID").

Holy cow. That sounds like a major uh.... hitch... if you want to use a hardware RAID card with ZFS.

Thanks for the link!

---

### Post by Vegan on 2013-07-02
ext4 works fine, use it, compatible with all raid cards and arrays

most uppity raid cards have a bios to work with too

---

### Post by rubylaser on 2013-07-02
> **Vegan said:**
> ext4 works fine, use it, compatible with all raid cards and arrays

most uppity raid cards have a bios to work with too

Very true, but the OP was talking about using NAS4Free, which uses ZFS by default, so I was just alerting him of the potential shortcomings.

---

### Post by nerdtron on 2013-07-04
> **rubylaser said:**
> Very true, but the OP was talking about using NAS4Free, which uses ZFS by default, so I was just alerting him of the potential shortcomings.

You're correct sir. And I'm aware of the hardware RAID problem. My 1st option before deciding RAID6 is to use JBOD (Just a Bunch of Disks) mode and then let ZFS (in RAIZ2 mode) do its thing. RAIDZ2 can be perform faster than RAID6 based on my readings.
But it seems that my current card doesn't support JBOD so I decided to use RAID6. Then again the NAS4Free server isn't deployed yet, and I think I'll wait for another server which we also ordered. I believe it can support JBOD and I'll swap their RAID controllers.

---

