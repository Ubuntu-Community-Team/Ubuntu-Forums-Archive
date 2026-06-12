---
title: "Ide Raid master/slave?"
date: 2008-10-05
forum: Server Platforms
---

### Post by jbarby on 2008-10-05
I am looking to setup a software Raid 5 + hot spare setup in the future. 

I have read that if you put drives in master/slave that if one fails it can affect the other and bring everything down. My situation is such that if 2 drives fail due to this and I am able to power down the system and replace the defective drive and bring all the data back up that would be fine. However if the data is lost due one drive corrupting the other or the OS will not allow this and causes the raid 5 to die completely I would pursue something else such as some sort of mirroring setup. Does anyone know how exactly the software RAID will fail in a master/slave setup?

Thanks

---

### Post by Krupski on 2008-10-05
> **jbarby said:**
> I am looking to setup a software Raid 5 + hot spare setup in the future. 

I have read that if you put drives in master/slave that if one fails it can affect the other and bring everything down.

A hard drive master / slave connection is electrical. A master hard drive mechanism could fail but the controller board will still "talk" to the slave drive.

Is there any way you could use SATA? That way, there's no worry about master / slave... each drive is connected to it's own port.

SATA drives are also more popular and probably cheaper too.

-- Roger

---

### Post by lykwydchykyn on 2008-10-05
I've definitely seen IDE problems that brought down the whole channel, and you don't want that to happen in a RAID situation.  Then again, I've lost RAID volumes on SCSI RAID 5 because the firmware in the backplane had a bug, so even a "pro" setup can have a potential failure point.  But IDE is not terribly robust as hard drive formats go.

IMHO if it's important enough to use RAID, get a good hardware RAID and SATA or SCSI drives.

---

### Post by jbarby on 2008-10-06
Here is a bit more background. 

At my work I am asking to get an old workstation they were going to throwaway and can re-purpose all the 40 gig IDE drives I want and SATA comes around once in a great while. Once I get the server I am going to rip it open to look at my options. If it has SATA ports at all I would like that to hold OS and services such as a web server, network time server, and mysql in software RAID 1. Then have a RAID 5 + hot spare portion on the IDE side of things and most likely it will have 2 channels for a maximum of 4 drives in a master/slave config as redundant place I can toss data. 

Thanks for the replies. It would be okay with me if in the event that a drive brings down a whole channel I could power it down and repair the 1 drive and bring the channel back up and let it rebuild. But if software kills itself cause 2 drives are missing and it is non recoverable as soon as 2 drives go i need to look into mirroring one channel against the other.

---

### Post by lykwydchykyn on 2008-10-06
If the channel becomes unavailable, that means 2 drives offline.  That's bad for RAID5, though I'm not sure if it'd be fatal in a 4 drive situation (can't quite manage the math for that one in my head).  Depending on the situation, it may come back online if you replace the bad drive, but how will you know which drive went bad?

I guess the only point I have is that this is maybe a step above a single drive, but it's still subject to a few more failure points than a SCSI setup.  You gotta work with what you got, though.

---

### Post by lykwydchykyn on 2008-10-06
If the channel becomes unavailable, that means 2 drives offline.  That's bad for RAID5, though I'm not sure if it'd be fatal in a 4 drive situation (can't quite manage the math for that one in my head).  Depending on the situation, it may come back online if you replace the bad drive, but how will you know which drive went bad?

I guess the only point I have is that this is maybe a step above a single drive, but it's still subject to a few more failure points than a SCSI setup.  You gotta work with what you got, though.

---

