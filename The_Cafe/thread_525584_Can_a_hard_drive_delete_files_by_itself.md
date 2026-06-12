---
title: "Can a hard drive delete files by itself?"
date: 2007-08-14
forum: The Cafe
---

### Post by FuturePilot on 2007-08-14
This is rather weird. I'm not sure where to put it since it has nothing to do with Ubuntu. So here's the story. I had built a Gnomad2 deb with MTP support for my Dapper machine along with a few others. After I installed them I had moved them over to my external hard drive in case I ever needed them again. Now I know they were there. Today I browsed into that directory accidentally where they were stored and....they were gone!! :o. All of them gone!

The reason I suspect the hard drive is because every so often it makes this horrible noise. It sounds like the read head is getting stuck or something and then goes scraping against the platter. It's a terrible sounding noise, it really is. But it's always done that ever since I got it about 2 or 3 years ago. So could that be causing a read error or something? Is that even possible?

Gahh, all that hard work I put into those debs:evil:

---

### Post by buzzmandt on 2007-08-14
sounds like a head crash, if your drive is going bad and losing sectors, information will dissapear

---

### Post by FuturePilot on 2007-08-14
Well something is wrong. I found the debs I built on a USB flash drive and when I tried to copy them over to my external hard drive I got an I/O error. Time for a new HD? :o

---

### Post by FuturePilot on 2007-08-14
> **buzzmandt said:**
> sounds like a head crash, if your drive is going bad and losing sectors, information will dissapear

That's what I was thinking. I've got a lot of backing up to do....

---

### Post by Bigbluecat on 2007-08-14
Certainly sounds like your hard drive is about to fail. I had one go like that (a windows drive). 

You can use Testdisk to try to check it and maybe recover some files.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It may be in the repos. If not it is on KNoppix and GParted LiveCDs. I used it to recover partition tables that got mangled by the failing drives.

---

### Post by skwishybug on 2007-08-14
Definitely sounds like your drive is about to fail. My wife's computer did similar recently (she runs windows) thankful for the LiveCD, allowed me to back up (most of) her files to a USB.
 
Then wiped and tried to rebuild. I was able to make a beautiful partition table but could not format or install to any of the partitions with either Ubuntu or Windows.
 
Gotta love warranties.

---

### Post by blithen on 2007-08-14
Yep, your HDD is defiantly going bad. You should have gotten a new one when it started doing that in the first place >_>

---

### Post by FuturePilot on 2007-08-14
Yeah I should have gotten a new one long ago. But it's always made that noise and this is the first time I'm having problems with it. It's always worked perfectly despite that awful noise. 0_o

---

