---
title: "should i run *any* updates to keep Ubuntu stable on production critical machine??"
date: 2009-09-22
forum: Ubuntu Studio
---

### Post by wentzr on 2009-09-22
I have a production critical machine which i use for low latency "real-time" audio work. I use renoise and ardour to create multitrack sample driven sequences of music, and also do a bit of recording with this computer. I'm using ubuntu studio, artistx and 64studio on this machine, it's a laptop with an echo indigo i/o. I've got mostly everything working, mostly... in each OS, but I'm curious.. what is the general consensus regarding running updates on a production critical release of ubuntu studio?! Should I run the recommended security updates only? or should I run *any* updates at all? I have a few dedicated machines that I would like to keep current, but most importantly they've gotta run like well oiled machines, all the time. 

I work also on a mac, and also on pcs... and I know the general consensus is if it ain't broke don't fix it. i did work on a red hat system running smoke and flint, we would only run updates when they had service packs to the software which required kernal updates, but everything came from autodesk... what's the recommendation for ubuntu studio? 

Thanks a lot, I'd love to get some feedback on this from some of the experts.

---

### Post by tgeer43 on 2009-09-23
This really depends on a lot of different things but generally speaking if it is stable now then the only updates that I would even consider is critical security updates. If the machine is not networked then I wouldn't even consider them.

tgeer

---

### Post by Stochastic on 2009-09-23
I've never known an update to break my system (not including development releases).

I assume that because your computer is aware of the updates, it's connected to the internet.  In that case, you really should at least install the security updates.

The other updates should all just be bug-fixes so if you're happy then there's no need to worry about fixing the bugs you're not running into.

I wouldn't start installing any backports though as these introduce new versions of software that could potentially injure your well oiled machine.

---

### Post by wentzr on 2009-09-23
> **Stochastic said:**
> I've never known an update to break my system (not including development releases)..

thanks, this is pretty much exactly the insight that i was looking for.. I felt what you've posted was pretty much the logical solution.. since it's on the Internet. I should at least be installing the critical security updates, but the info regarding updates breaking something was what I was after. 

I suppose the other part of the question was wondering if there might be a chance that I could be installing an update that will over-write a config file that had been tuned from the original distribution. I don't want to do that and I have no idea what files have been configured and... "oiled". 

still related... I've been digging around on backing up your system. ehm.. couldn't i just attach removable media with a large ext3 partition, boot from a live disk (or a different linux partition on the drive), and copy ALL the destination files using rsync in a terminal as root to the removable ext3 partition??

---

### Post by Bucky Ball on 2009-09-23
I set up a computer for a family around the corner about three months ago and they are not online so no updates. The machine is as rock solid as the day I dropped it off.

---

### Post by tgeer43 on 2009-09-23
> **Stochastic said:**
> I've never known an update to break my system (not including development releases).
You've been running Ubuntu for at least 3-1/2 years and you've never had an update break anything? I'd say you've led a charmed life and are in the vast minority. Sure, it doesn't happen very often but it definitely *does* happen.

tgeer

---

### Post by wentzr on 2009-09-23
this is why forums are a good thing. thanks for the info. i'm going to be keeping the laptop offline, w/ each OS installed directly from the live cd, w/ no updates, just my own edits to a few .conf files. . . 
i have this (desktop next to production machine) computer for internet and testing... so problem solved.. i'll just set up file sharing between the two.

---

### Post by Stochastic on 2009-09-23
> **wentzr said:**
> i'm going to be keeping the laptop offline,
<snip>
 i'll just set up file sharing between the two.

Um, if you're setting up file sharing, then chances are your computers will both be plugged into your router.  I'm going to assume you also have the internet hooked into your router.  If both of those conditions are true, then I'd recommend downloading the security updates at least.

---

### Post by Bucky Ball on 2009-09-23
> **Stochastic said:**
> Um, if you're setting up file sharing, then chances are your computers will both be plugged into your router.  I'm going to assume you also have the internet hooked into your router.  If both of those conditions are true, then I'd recommend downloading the security updates at least.

+1

If you are networking and either computer is online make sure that one (or both if both online) get at least security updates.

---

### Post by mcduck on 2009-09-24
> **tgeer43 said:**
> You've been running Ubuntu for at least 3-1/2 years and you've never had an update break anything? I'd say you've led a charmed life and are in the vast minority. Sure, it doesn't happen very often but it definitely *does* happen.

tgeer

Then there's lot more of us :)

I've never had any problems, apart from the ones I've caused myself or by running development release.

Most people who I've seen having issues with updates have installed stuff (like nVidia drivers..) from outside of Ubuntu's repositories.

---

### Post by FakeOutdoorsman on 2009-09-24
> **wentzr said:**
> still related... I've been digging around on backing up your system. ehm.. couldn't i just attach removable media with a large ext3 partition, boot from a live disk (or a different linux partition on the drive), and copy ALL the destination files using rsync in a terminal as root to the removable ext3 partition??
Just mount your external drive and run *rdiff-backup* (it's in the repository) or any number of similar scripts with cron for daily, automated, and incremental backups.  Incremental being key.  How many of us have overwritten our backups with a messed up file from the production computer?  For your system configs, you can simply copy all of */etc* which is usually < 20 MB anyway.

Even better are off-site backups.  Four years ago my work building almost burned down.  Did I have off-site backups?  No.  I do now.

I use *duplicity* for my backups.  It's rdiff-backup's cousin.  Main difference is duplicity adds encryption and is a little harder to use.

---

### Post by TheBuzzSaw on 2009-09-24
Consider focusing on updating between major projects. I'm not sure if you have any such down time, but if you can, update during transitions so you don't ruin any in-progress stuff. At worst, you delay the start of a new project for a bit; at least the previous one will be done.

---

### Post by wentzr on 2009-09-25
> **mcduck said:**
> Then there's lot more of us :)
Most people who I've seen having issues with updates have installed stuff (like nVidia drivers..) from outside of Ubuntu's repositories.

bingo.. yes indeed... i've yet to be able to even install the nvidia driver on ubuntu studio 9.04 successfully... always ends with an ultimately unbootable partition. . kinda a bummer as I'd love to use two monitors, but i've just kept *that* xorg.conf alone.

---

### Post by wentzr on 2009-09-25
> **FakeOutdoorsman said:**
> Just mount your external drive and run *rdiff-backup* (it's in the repository) or any number of similar scripts with cron for daily, automated, and incremental backups.  Incremental being key.  How many of us have overwritten our backups with a messed up file from the production computer?  For your system configs, you can simply copy all of */etc* which is usually < 20 MB anyway.

Even better are off-site backups.  Four years ago my work building almost burned down.  Did I have off-site backups?  No.  I do now.

I use *duplicity* for my backups.  It's rdiff-backup's cousin.  Main difference is duplicity adds encryption and is a little harder to use.

thanks a ton for this (current) suggestion. seems from searching various forums that there are many "best" ways to do archive a system.. but yeah, running into a situation like you did is what I always like to avoid.. Sorry to hear about that, Things like that are bound to keep some people up at night! I've been using dropbox for most of my crucial file backups... pretty dead simple innexpensive tool, and free if you don't need more than 2gb of backup.

And yeah I agree with buzz on updating between projects... I never ever EVAR update during projects. I used to work as a field tech support dude, demoing, fixing and installing advanced systems for film/broadcast.. can't tell you how many times people lost partitions or RAIDs when updating something... even as "little" as quicktime.

---

### Post by wentzr on 2009-09-29
Found this site
[http://www.boomerclan.info/](http://www.boomerclan.info/)

an interesting paper dealing with the whole topic, also a useful backup strategy.

---

### Post by brian mcgee on 2009-09-29
I manage several Ubuntu, Debian and CentOS  production servers at work, and like most people are saying, at least do the security updates. I've never once had an update break anything that I know of...

---

