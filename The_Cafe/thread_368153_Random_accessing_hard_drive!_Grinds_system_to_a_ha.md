---
title: "Random accessing hard drive! Grinds system to a halt."
date: 2007-02-22
forum: The Cafe
---

### Post by sandrogalli on 2007-02-22
I have found, in pretty much all the OS's that I have used (Windows, and various linux distributions) that every so often, and it seems completely randomnly, that all at once the computer will start making that "clicking" sound as if it is accessing the hard drive; unzipping a large archive or something like that. The peculiar thing is, that this often happens when you have minimal load on your cpu. Just today, I was happily browsing in Firefox (in ubuntu) when I hear that dreaded clicking sound start to build up and then get to a stage when it effectively ground my system (2ghz Mobile Pentium, 1gb RAM) to a halt. It continued to do this for around an hour or so at which point I got so frustrated I hit the power and rebooted. On startup once again everthing seems to be working smoothly. No missing files, no corrupted data etc...

Does anyone actually know what is the reason for this apparently random behaviour. I am almost certain that no activity was going on in the background nor was there any task scheduled for that time!!

---

### Post by The Noble on 2007-02-23
Almost sounds like the signs of a soon-to-be hard drive failure. Backup everything you have often, because you don't want it to finally die on you. Hopefully I am wrong though...

---

### Post by Phatfiddler on 2007-02-23
Thw Noble may be on to things.  I had the exact same thing not too long ago when I used XP.  Turns out I had system files on bad sectors.  Wiped out the hard drive, cleaned it up, reinstalled XP, and never had problems since.  Of course, I now run Linux and am still trouble-free.

---

### Post by The Noble on 2007-02-23
Heh, about a year ago I was having problems with a brand new hard drive. I had installed windows over seven times because it would boot after a few days and not recognize itself. For a temporary relief, I installed Ubuntu 5.04, and it lived for about two weeks until I had to get another hard drive that could run windows faithfully (for the family). Moral of the story is, sandrogalli, linux handles bad sectors better than windows; once even linux fails though, you are in the dog house. Maybe you could download a hard drive checker (from the manufacturer's site) to see if we are right or wrong.

---

### Post by sandrogalli on 2007-02-23
Jeez! Lucky I posted... I was actually kinda expecting a logical answer that I had simply overlooked. Come to think of it, it has been doing it more frequently recently; ill definitely give the HD a backup and a scan.

Tnx for the heads up!

---

### Post by prizrak on 2007-02-23
Grab the ultimate boot cd (exact name just Google it) and check your drive. The click of death is a common sign of the drive dying as is decreased performance. 

Windows's random HDD accessing and slowing the system down is due to the Indexing Service trying to index the drive (I generally turn it off). 

Ubuntu's random HDD accessing and slowing the system down is the update agent refreshing your repositories. This should normally only happen couple of minutes after boot. 

> Moral of the story is, sandrogalli, linux handles bad sectors better than windows;
Linux tends to load the kernel at boot and keep it in RAM so unless your kernel is on bad clusters you won't see a problem until the OS tries to swap into bad space or access something that sits on bad space.

---

### Post by SuperMike on 2007-02-23
My experience has been that clicking sounds are when the drive is about to blow. Best to get off that system and onto a new hard drive ASAP.

---

### Post by sandrogalli on 2007-02-23
> Windows's random HDD accessing and slowing the system down is due to the Indexing Service trying to index the drive (I generally turn it off).

I knew it was something silly like this...

> Grab the ultimate boot cd (exact name just Google it) and check your drive. The click of death is a common sign of the drive dying as is decreased performance.

Ok, so I downloaded this, as I am a little worried about my HD now (its a laptop that I leave on 24/7, so I guess wear and tear is definitely a possibility). The problem is, I have no way of finding out which brand the hard drive is. I've checked the documentation, had a look around on the internet and even opened up my laptop but no sign of a brand. The various tools on UBCD dont seem to detect my particular HD and most actually crash out. I've tried PowerMax, SeaTools and Western Digitals and a few others.

Are there any such utilities that are made especially for notebook drives? Or is it possible for me to run a surface scan natively within a session?

Thanks for all the help.

---

### Post by prizrak on 2007-02-24
> **sandrogalli said:**
> I knew it was something silly like this...



Ok, so I downloaded this, as I am a little worried about my HD now (its a laptop that I leave on 24/7, so I guess wear and tear is definitely a possibility). The problem is, I have no way of finding out which brand the hard drive is. I've checked the documentation, had a look around on the internet and even opened up my laptop but no sign of a brand. The various tools on UBCD dont seem to detect my particular HD and most actually crash out. I've tried PowerMax, SeaTools and Western Digitals and a few others.

Are there any such utilities that are made especially for notebook drives? Or is it possible for me to run a surface scan natively within a session?

Thanks for all the help.
If you downloaded the full UBCD it should have a generic program that will be able to scan any drive. The name completely escapes me at the moment. Laptop drives are generally Toshiba or Hitachi older ones are IBM. I'll dig around for my UBCD and let you know what the name of the program is.

---

### Post by sandrogalli on 2007-02-24
Ok, so i ran an app called "salvation scan and repair" and it didnt pick up any errors! Of course thats great, but my system froze up for a good half and hour today clicking away, and now im just puzzled.

I was running a few gaim windows, firefox and openoffice... is it possible for the system to lock up like this (literally unusable until it finishes accessing the HD) because of the demand on resourses?

Oh, also i do have a rather complicated partition table at the moment; fat32, ext3, swap and fat32 in that order. Could that have anything to do with it?

really just curious what could be causing my comp to do this atm...

---

### Post by funchords on 2007-02-25
> **sandrogalli said:**
> Ok, so i ran an app called "salvation scan and repair" and it didnt pick up any errors! Of course thats great, but my system froze up for a good half and hour today clicking away, and now im just puzzled.

I know that you just tested it, but trust me that this is a failing HDD.  Spend its last remaining hours doing a backup, while you can.  Then get a replacement -- hard drives have never been cheaper than they are right now.  

The reason this is intermittent is because the bad sector is unallocated.  Your system eventually tries to write to the unallocated sector, and finds that the data was not recorded right.  So then it tries again, and again, and again.  And the reason for the little hang is because these are done through BIOS calls, and every freakin' little efficiency and security utility has glommed itself over the top of those calls (not so much a problem in Linux as in Windows).  But your software isn't going to continue until your hardware is happy.

These problems also grow.  Temperature and grime make slight changes to where on the platters the data is written and read.  A sector could be readable/writable one moment, and out of bounds at the next.  

There are products that detect this kind of thing, but in order to do it, they make repeated writes and reads of data patterns to the drive.  You won't detect this kind of problem with error checkers that only read allocated sectors and check linking.

So, in short, if it's clickin' it's time is tickin' -- get your data off of it and get a new drive.  I've never seen a clickin' HDD brought back to health -- and I've been doing this since the marble and chisel days.  :-)

Robb

---

### Post by funchords on 2007-02-25
> **sandrogalli said:**
> 
Oh, also i do have a rather complicated partition table at the moment; fat32, ext3, swap and fat32 in that order. Could that have anything to do with it?

Sorry, I forgot to answer this.  No, your partition combination is no problem.  It would not be the cause of this behavior.

---

### Post by TravisNewman on 2007-02-25
When you say clicking do you mean literal clicking or more grinding, like normal data writing sounds only more intense? That could be the difference between a failed hard drive and just one you need to wipe and start fresh with. If it's literally clicking, about once every second, the drive is about to die. If it's the hard drive grinding noise it may be getting tired but it's not about to die.

---

### Post by mips on 2007-02-25
> **sandrogalli said:**
> The problem is, I have no way of finding out which brand the hard drive is. 

Check the BIOS. Alternatively pull the HD out when the laptop is off & battery removed. Should be easy to remove, usually just one screw or so.

If you replace the drive get a Hitachi Travelstar 7200rpm.

---

### Post by bonzodog on 2007-02-25
Whats the exact make & Model of the Laptop itself?

We might be able to tell you what to buy from that.

But, yes, your hdd is almost dead. time to chuck it, and install a new one.

---

### Post by sandrogalli on 2007-02-25
Hey guys, thanks for all the great advice, gotta love these forum thingies.

> The reason this is intermittent is because the bad sector is unallocated. Your system eventually tries to write to the unallocated sector, and finds that the data was not recorded right. So then it tries again, and again, and again. And the reason for the little hang is because these are done through BIOS calls, and every freakin' little efficiency and security utility has glommed itself over the top of those calls (not so much a problem in Linux as in Windows). But your software isn't going to continue until your hardware is happy.

You know, I bet thats it. Just what I wanted to know, thanks.

> When you say clicking do you mean literal clicking or more grinding, like normal data writing sounds only more intense? That could be the difference between a failed hard drive and just one you need to wipe and start fresh with. If it's literally clicking, about once every second, the drive is about to die. If it's the hard drive grinding noise it may be getting tired but it's not about to die.

Kinda hard to describe and make sure you know what I mean... you might be onto something with the "grinding", its the noise that it makes when you are rar'ing/un'raring a large archive, or defraggin in XP. Seems to happen more often now and at complete random, and has happened twice in the last three days. It "grinds" away for a good hour or more without any change (although I still have mouse movement, tho severely delayed) at which point I've powered off and rebooted (gotta work). The system seems to work fine at all other times. I wouldn't say there was a really unhealthy "clicking", although I've never experienced this before so I've only my imagination to compare it to.

In any case I've set my sights on a new 80gb as I need the space anyway, I was thinking of getting a fujitsu 5400rpm as a local retailer has them at a pretty good price. I have a Toshiba Satellite 2410-603 BTW.
> 
If you replace the drive get a Hitachi Travelstar 7200rpm.

Is there any particular reason for this? And does anyone know what kind of a performance gain 7200 has over 5400?

I'm full of questions I know, I'll stop soon I promise ;)

---

### Post by mips on 2007-02-26
> **sandrogalli said:**
> 
Is there any particular reason for this? And does anyone know what kind of a performance gain 7200 has over 5400?


I've had some interaction with data recovery companies and if anybody should know about drives it is these guys. They see it all everyday, dissasemble them in a clean room environment etc.

I asked them what they recommended as replacement drives from the perspective of least failures & easiest to recover data from if failed. For 2.5" the guys swore by Hitachi and cursed Seagate. I myself sent several 2.5" seagate drives of to them for data recovery. These were replaced by Hitachi and still purring along nicely.

For 3.5" drives they recommended Seagate & WD. I actually wrote down a list of good and bads but cannot find it right now.

My experience with Fujitsu to date has been a mixed bag of failures & successes.

7200rpm should give you a noticeable speed improvement when it comes to drive performance. I don buy any drives below 7200rpm anymore. The bigger the cache the better as well.

---

### Post by OrangeCrate on 2007-02-26
> **sandrogalli said:**
> Ok, so i ran an app called "salvation scan and repair" and it didnt pick up any errors! Of course thats great, but my system froze up for a good half and hour today clicking away, and now im just puzzled.

I was running a few gaim windows, firefox and openoffice... is it possible for the system to lock up like this (literally unusable until it finishes accessing the HD) because of the demand on resourses?

Oh, also i do have a rather complicated partition table at the moment; fat32, ext3, swap and fat32 in that order. Could that have anything to do with it?

really just curious what could be causing my comp to do this atm...

As others have said, YOUR HARD DRIVE IS FAILING. Follow the advice given to you above regarding backing up your important data - today if possible. Recovery of data from a failed drive is costly.

---

### Post by UniRecovery on 2007-02-26
This click is also known as "the click of death", which indicates extensive head damage. If you hear it you should stop the drive immediately, and I would not advise you to boot from it again, otherwise the platters will be burnt by the damaged head. DO NOT OPEN UP THE DRIVE CASING, send it to a professional data recovery company.

---

### Post by sandrogalli on 2007-02-26
> For 3.5" drives they recommended Seagate & WD. I actually wrote down a list of good and bads but cannot find it right now.

I can vouch for Seagate too, I once knocked a barracuda of the top of a machine. I must have fell about 5 feet but that rubber casing seemed to have done its job, as it's still going a year later. Thanks for all the info mips, really good advice. Oh and if you find that list of hard drives, post it up, it could help any future wanderers who stumble across this thread.

Ok, so I've ordered an new 100gb Hitachi, and it should be here in the next few days. I've backed up all the data I need to DVD, and I've started loading knoppix for general computer use just in case. I think that HD might have been getting a little tired, although it served me well a good few years! I think I might write zero's to the whole disk and see if that improves anything, just in case it is a filesystem error and not a physical one. Funny thing is, if this was Windows I would have just put it all down to a badly designed OS but it was because I was used to ubuntu running so smoothly that I really took notice. In any case, I just wanna thank all of you for the help and advice!

---

### Post by mips on 2007-02-26
As a laptop user another nice idea is to get an external 3.5" HD + Enclosure. Best interfaces to that would be External Sata (eSata) or Firewire(800). USB does not hold a candle to the above two.

---

### Post by jdong on 2007-02-26
Ubuntu Edgy and beyond use CFQ (Complete Fair Queuing) IO scheduling, so no amount of disk traffic can make one program completely unresponsive.

If that's happening and you're hearing repetitive disk clicks, then it's probably your hard disk ready to fail (re-reading a track).

Most hard disks will not correct read failures with a reserved sector -- only write failures... In other words you MAY be able to squeeze some more time out of your drives by backing up,  wiping it a few times (**sudo dd if=/dev/zero of=/dev/drive**, repeat) and restoring all your data to it.

But in all seriousness, it's time to back up and shop for another hard drive. I've personally had very good luck with Seagate and WD, terrible luck with Maxtor and IBM

---

