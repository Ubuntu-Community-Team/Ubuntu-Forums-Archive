---
title: "Quick RAID question"
date: 2009-11-11
forum: Server Platforms
---

### Post by zoomiest on 2009-11-11
I just acquired a Dell PowerEdge 1800. It has a RAID configuration.
(one 200 GB drive on ATA, and 5 200 GB drives on CERC)

So, I guess I install the OS on the single drive, and configure the RAID of the data...

Right? (please confirm)

---

### Post by DJ_Max on 2009-11-11
Hardware or software?

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by zoomiest on 2009-11-11
Its a hardware RAID

its really an architecture type of question... how do I lay this out?

---

### Post by DJ_Max on 2009-11-11
Have you tried installing yet? You should be able to pop in the CD/DVD, and configure it on the install.

---

### Post by zoomiest on 2009-11-11
Yes, I have tried installing. I actually can install it, but then, I have trouble with the GRUB installer, and I can't get to any prompt to manually fix it.

Now, my box boots up - the bios boots, then comes to point where it says GRUB, but its not a prompt, so I can't do anything... as is suggested above (with the software RAID).

I am working on a  hardware controlled, RAID5 (Dell PowerEdge 1800 with 5 Raided SATA drives, and one other drive.

A funny thing is that the HDD boot order didn't seem to work when I put the single drive first. It only boots up completely when the RAID array is first in the HDD boot order. Any help here?

So, my question is ... how do I get this machine to boot up - at least to a commandline, where I can configure GRUB?

---

### Post by AgentZ86 on 2009-11-11
Can you turn off your hard raid and use soft raid or do you prefer hard raid ?

But you don't want both, thats the main thing

Also you may want to move drives around, to be sure you don't already have a drive with a failed boot sector ?, just a thought

---

### Post by viper250 on 2009-11-11
on the dell poweredge servers use the hardware raid as it is more reliable ( software raid configuration files can easily be corrupted and you can loose access to your data), select the boot driveand flag it as boot,  all the drives need to be configured properly and initialized for its raid configuration.
my own server uses scsi drives and a hardware raid controller once the drives were configured I installed ubuntu server works like a charm
Dell Poweredge 2800, dual 3.4 ghz 8 gig ram, and 8 160 gig hdds ( planning to install fiberoptic to use this machine as mirror site

---

### Post by AgentZ86 on 2009-11-13
> **viper250 said:**
> on the dell poweredge servers use the hardware raid as it is more reliable ( software raid configuration files can easily be corrupted and you can loose access to your data), select the boot driveand flag it as boot,  all the drives need to be configured properly and initialized for its raid configuration.
my own server uses scsi drives and a hardware raid controller once the drives were configured I installed ubuntu server works like a charm
Dell Poweredge 2800, dual 3.4 ghz 8 gig ram, and 8 160 gig hdds ( planning to install fiberoptic to use this machine as mirror site

Hi viper250,

I am transitioning from SME, and I don't really know enough about raid to say whether soft raid or hard raid is better, but according to SME soft raid is better, however I guess it would depend on the quality of the hard raid card too ?

Anyhow, I don't mean to butt in on this post, but I'm curious about your hard raid setup ?
Hard raid sounds simpler ? 

So lets say you have a drive go bad on your setup ? Do you just popin a new drive Or do how much work is it for you to address a failed drive that my biggest concern. I don't want to be messing around with too much command line to try and mda the drive back into the failed raid ?

I'm considering a simple setup with just maybe 2) scisi drives in an older server perhaps, or maybe one of those old compaq boxes with a bunch of 72gb drives or something. But in any case I want the most headache free method ?

Can you advise on that topic a bit please
Thanks

---

### Post by JonRohan on 2009-11-13
> **AgentZ86 said:**
> Hi viper250,

I am transitioning from SME, and I don't really know enough about raid to say whether soft raid or hard raid is better, but according to SME soft raid is better, however I guess it would depend on the quality of the hard raid card too ?

Anyhow, I don't mean to butt in on this post, but I'm curious about your hard raid setup ?
Hard raid sounds simpler ? 

So lets say you have a drive go bad on your setup ? Do you just popin a new drive Or do how much work is it for you to address a failed drive that my biggest concern. I don't want to be messing around with too much command line to try and mda the drive back into the failed raid ?

I'm considering a simple setup with just maybe 2) scisi drives in an older server perhaps, or maybe one of those old compaq boxes with a bunch of 72gb drives or something. But in any case I want the most headache free method ?

Can you advise on that topic a bit please
Thanks

You should always use a decent hardware RAID card. It is generally more reliable and will offer better performance. 

If a drive fails in the array and you have hot swap support on your server you can swap out the drive without downtime and whilst the server is running. Some cheaper servers will not have hot swap capability and will require the server to be shutdown. You can replace a hot swap drive using software RAID too IIRC. 

Just do confuse you more you can have hot spare drives to in which in effect lay dormant ready for a failure and kick into life. This pretty good for RAID sets that can only survive one failure as you are instantly rebuilding the array.

---

