---
title: "Program to monitor bandwidth?"
date: 2008-09-10
forum: The Cafe
---

### Post by dbbolton on 2008-09-10
My ISP, who shall remain nameless, is implementing a 250GB/mo. cap effective 1 October 2008. However, they offer no service to monitor monthly bandwidth consumption. Instead, they recommend "downloading a program" to do it. I would like to know whether such a program exists for Ubuntu.

I was hoping for some sort of daemon (perhaps something like whatever conky uses to monitor network traffic) that would work in the background and save relevant data in a log file. 
 
Ideally, it would also compose and print colorful, helpful charts, and make coffee.

---

### Post by niko7865 on 2008-09-10
Sure is nice of Comcast to do that to you. If you have a router, I suggest seeing if you can install Tomato or DD-WRT onto it, both of those can monitor total usage for all computers in your dwelling.

---

### Post by dbbolton on 2008-09-10
Hmm. I'm not sure how I feel about messing with router firmware. I might try this out if I get a "warning letter". Apparently, my service will be permanently disconnected if I require a second warning.

---

### Post by stmiller on 2008-09-10
DD-WRT has excellent bandwidth graphs, and such.

I am a fairly heavy internet user and use 20-30GB a month. 250GB is a LOT.

Installing DD-WRT is easy- just click to 'upload' the dd-wrt file inside the router upgrade section of your router software. And bingo you have a $300 router.

---

### Post by dbbolton on 2008-09-10
> **stmiller said:**
> DD-WRT has excellent bandwidth graphs, and such.

I am a fairly heavy internet user and use 20-30GB a month. 250GB is a LOT.

Installing DD-WRT is easy- just click to 'upload' the dd-wrt file inside the router upgrade section of your router software. And bingo you have a $300 router.
I guess a lot hangs on whether or not your Wifi has a password :D

---

### Post by zmjjmz on 2008-09-11
Oh come on, installing DD-WRT is not that easy.
I tried it and failed, luckily I didn't brick my router.
But I won't need to monitor bandwidth, because we're definitely switching to FiOS.

---

### Post by ad_267 on 2008-09-11
I use vnstat to monitor mine, it's command line only but I've got it set up to appear in conky. I only have a 20 Gig cap though, 250 would be pretty good!

sudo apt-get install vnstat
sudo vnstat -u -i eth0

then wait 10 mins:

vnstat

Edit: I explained the conky stuff here: [http://ubuntuforums.org/showthread.php?t=837658&page=2](http://ubuntuforums.org/showthread.php?t=837658&page=2)

Oh yeah and if you like pretty graphs, just run:
vnstat -h

---

