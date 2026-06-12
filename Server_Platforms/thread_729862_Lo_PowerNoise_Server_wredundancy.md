---
title: "Lo Power/Noise Server w/redundancy?"
date: 2008-03-20
forum: Server Platforms
---

### Post by ryth on 2008-03-20
Hi folks,

As per [**this link**]("http://ubuntuforums.org/showthread.php?t=713201") I'm looking to create a server to do the following:

A.  Filleserver (for video media primarily)
B.  Email server
C.  (potentially) act as an ftp server (sporadically)
D.  (potentially) run as RAID

The criteria I'd be basing my mobo choice on would be:

1.  Power consumption
2.  Noise
3.  Profile

Now I was thinking of running RAID 5 on the server to provide redundancy, but I'm not sure if that can jive with criteria 1,2,3?

In the thread linked above it was suggested that a Via Epia chip might be ideal for this, however having looked over the specs on the Epia chip it doesn't look possible to do a RAID set up, and also having the RAID would obviously defeat the great small form factor of the mini-ITX.  Also what is Ubuntu Server compatibility like with the Via Epia boards?

Am I up a creek without a paddle in being able to build something that isn't a total hog with power and heat,. yet wanting the redundancy?  I have a pretty small operating space physically so having a third machine to run as a backup and abandoning the RAID idea isn't really an option, and obviously conflicts with the want for lower power consumption.

Any sort of creative solutions are welcomed that might help me meet the above criteria and priorities.

Cheers.

---

### Post by smileypaul on 2008-03-20
You could probably grab an old ReadyNAS box from Ebay.

even just the box..and fill it with hard drives of your choise.

They are small, use RAID 5, and are quiet.. so it does meet your needs.

My only complaint is that the web interface can be slow.

Its basically a small install of linux, use for file sharing purposes.. ftp, and rsync are also available on it, as well as shell access through ssh. Do some research, the one i have has Gigabit ethernet, and many great options.


edit: sorry, didnt see the email portion. This box would be no good for this. You may want to look into a box that supports 4 disks for RAID5.. shouldnt be hard to find.

---

### Post by ryth on 2008-03-20
> **smileypaul said:**
> You could probably grab an old ReadyNAS box from Ebay.

I was thinking of a ReadyNAS box, but I feel like it is going to cost me more and not offer the sort of modularity that I'd like.. Plus the email server idea kind of puts the axe to it.  They are handy little buggers though.

Again I realise it would be easy to just set up an old box and have it ready to go, but I'd really like to focus on the lower power and low noise factors.

---

### Post by tgalati4 on 2008-03-20
I have an epia 1 GHz machine that I used for embedded device work.  They are quiet and only draw around 12 watts in use and 2 watts in idle.  I have thought about doing something similar, but perhaps a combined solution--mini-ATX machine for your web/email serving and a NAS for file serving/backup/redundancy.

As energy prices go up, a 24/7 server will eat up some watts and the energy savings alone from these small machines will pay for themselves in 2 to 3 years.

You can use the epia with an external USB drive (mine has 4 USB ports).  Hang two drives and use one for a nightly mirror of the other.  This has the advantage of drive spin-down and cron scheduling to save power on the file serving end as well.

---

