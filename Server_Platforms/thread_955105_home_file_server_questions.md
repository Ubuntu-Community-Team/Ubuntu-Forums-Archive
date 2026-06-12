---
title: "home file server questions"
date: 2008-10-21
forum: Server Platforms
---

### Post by P86 on 2008-10-21
I'd like to start off by saying I'm a linux novice (a little better than a noob:). I've been fed a steady diet of Windows my whole life, but I'm learning. Currently, my file server is a FreeNAS box. FreeNAS is good, but definitely has some limitations.

So far I have managed to install Ubuntu Server 8.10, ACPI (and standby actually works!), and Webmin without major issues. I even got a basic file share working.

My hardware is a P3 650mhz with just less than 1gb of RAM (yeah, I know....its old).

My next project is RAID 1. My questions are:

1. Can you pair different size drives successfully? For example, drive A is 160gb, and drive B is 60gb. Can I partition drive A into two partitions, one with 100gb and one with 60gb and set up the second partition to mirror drive B? As well as continue to use the 100gb partition as non-redundant space?

2. Is there any advantage to hardware RAID over software RAID? (ie. flexibility, performance).

3. Filesystems. Wikipedia has some nasty things to say about ext3. Should I consider JFS or XFS? Reliability is obviously a concern on a file server.

I'm also sure I have other questions I can remember right at the moment! I appreciate your help and opinions.

---

### Post by lykwydchykyn on 2008-10-22
1. I'm not an expert at software RAID, but I believe this can be done.  Someone else may want to chime in on that.  But it kind of defeats the purpose, does it not?  I mean, are you going to mirror the system or the data?  And if your 160GB drive fails, either the system is down (if you're mirroring only data) or the data is lost (if you're mirroring only the system).  IMHO RAID is about availability, it's not a replacement for regular backups.  YMMV.

2. I don't know that I'd put much stock in software RAID, but I don't have metrics on that so I won't try to dissuade you.

3. In 5 1/2 years of using Linux, maintaining somewhere in the neighborhood of 30-40 boxes now, I'm trying to think of an incident where ext3 let me down.  Nope, can't think of one. JFS was problematic for me once, but that probably had more to do with using it on an iSCSI partition on an old version of SLES whose iSCSI driver wasn't quite ready for prime time (stupid thing wouldn't unmount the filesystem, even after syncing half a dozen times and starting a shutdown).

---

### Post by cariboo on 2008-10-22
I use the onboard raid controller of my motherboard, when I first set it up it wouldn't let me use hdd's from two different manufacturers as the geometries were different, so I had to put it off until I could get a matching hard drive from my supplier. I have since upgraded it to a pair of 500Gb hard drives, they are formatted as ext3 and have been running for about two years with absolutely zero problems.

Jim

---

### Post by P86 on 2008-10-22
> **lykwydchykyn said:**
> 1. I'm not an expert at software RAID, but I believe this can be done.  Someone else may want to chime in on that.  But it kind of defeats the purpose, does it not?  I mean, are you going to mirror the system or the data?  And if your 160GB drive fails, either the system is down (if you're mirroring only data) or the data is lost (if you're mirroring only the system).  IMHO RAID is about availability, it's not a replacement for regular backups.  YMMV.


I realize that it's not exactly an idea setup, but at the moment, until I can afford some more drives, I may have to settle. I am planning on mirroring the data on the premise that if I lose the system, I would still be able to rebuild the server and the RAID array, and recover the data. Is this a resonable assumption? Obviously, periodic backups are essential. But I am trying to add a some protection between backups.

---

### Post by lykwydchykyn on 2008-10-22
Well, then, instead of going through the pain of mirroring them, why not just schedule a nightly backup instead?  That way, you not only have a backup of your data, but if you delete or corrup a file, you can always retrieve yesterday's version.  

How much data do you have involved here?

---

### Post by doogy2004 on 2008-10-22
> **P86 said:**
> I'd like to start off by saying I'm a linux novice (a little better than a noob:). I've been fed a steady diet of Windows my whole life, but I'm learning. Currently, my file server is a FreeNAS box. FreeNAS is good, but definitely has some limitations.

So far I have managed to install Ubuntu Server 8.10, ACPI (and standby actually works!), and Webmin without major issues. I even got a basic file share working.

Congradulations, and good luck.

> **P86 said:**
> My hardware is a P3 650mhz with just less than 1gb of RAM (yeah, I know....its old).

I'm running my fileserver with Ubuntu server on a 330MHZ with 512MB Ram.  That barely has a load average of 0.01. So your hardware is more than enough.

> **P86 said:**
> My next project is RAID 1. My questions are:

1. Can you pair different size drives successfully? For example, drive A is 160gb, and drive B is 60gb. Can I partition drive A into two partitions, one with 100gb and one with 60gb and set up the second partition to mirror drive B? As well as continue to use the 100gb partition as non-redundant space?

In theory you can do that, because in Linux everything is a file.  Including all hardware and hard disk partitions.  I'm going to say that it is possible at this point, however I have never tried it but it should not be a problem.  When I was learning how to configure software RAID I was told that this was possible.

> **P86 said:**
> 2. Is there any advantage to hardware RAID over software RAID? (ie. flexibility, performance).

I'm using software RAID because I'm cheap and I don't have room in my box for a raid controller.  Hardware controllers give better performance because all of the calculations are performed on the controller rather than on the CPU.  Software RAID in my opinion is more flexable, because you can include disks of different sized in the RAID array.

> **P86 said:**
> 3. Filesystems. Wikipedia has some nasty things to say about ext3. Should I consider JFS or XFS? Reliability is obviously a concern on a file server.

I've never had trouble with EXT3.

> **P86 said:**
> I'm also sure I have other questions I can remember right at the moment! I appreciate your help and opinions.

When you remember the questions, don't be afraid to ask.

---

### Post by P86 on 2008-10-24
> **lykwydchykyn said:**
> Well, then, instead of going through the pain of mirroring them, why not just schedule a nightly backup instead?  That way, you not only have a backup of your data, but if you delete or corrup a file, you can always retrieve yesterday's version.  

How much data do you have involved here?

Not a ton of data. Only maybe 100gb. Mostly pictures, MP3s and some camcorder video. What do you suggest as a simply backup program? I was using RAID to avoid having another step to perform, because setting up a nightly backup would be overkill for the amount the server gets used. Basically, I dump pictures on it infrequently, but I suppose I could run a backup as soon as I make major changes. Otherwise, I want it to sit idly by in standby (suspend-to-RAM) mode.

---

### Post by P86 on 2008-10-24
> **doogy2004 said:**
> 
When you remember the questions, don't be afraid to ask.

4. Any idea how to get the server to standby (suspend-to-RAM) after a certain period of inactivity? Also, when in standby, would it be possible to wake the server using wake-on-LAN? I've used WOL in FreeNAS to boot the server when powered off, but I've never tried a machine in standby. I assume it would work the same.

---

### Post by lykwydchykyn on 2008-10-24
Backup can be as simple as putting an rsync command in your cron (command scheduler) list.

---

### Post by gpsmikey on 2008-10-25
Make sure your backups are to a physically different drive, not just a different partition.  If they are on the same drive (even if different partitions) and the drive fails, you lose (just had a Seagate 160 gig SATA drive at work fail with a noisy death and no data was recoverable (unless you send it to one of those $$$ places, then it might have been))

mikey

---

### Post by P86 on 2008-10-26
At this point I'm undecided if I should go with RAID or the backup route. Because I might end up changing drives again in the near future, I might try the backup route. Has anyone used Webmin for backups?

---

### Post by doogy2004 on 2008-10-26
> **P86 said:**
> At this point I'm undecided if I should go with RAID or the backup route. Because I might end up changing drives again in the near future, I might try the backup route. Has anyone used Webmin for backups?

I use Webmin to monitor my system.  I perform all of my administration by hand via SSH.

---

