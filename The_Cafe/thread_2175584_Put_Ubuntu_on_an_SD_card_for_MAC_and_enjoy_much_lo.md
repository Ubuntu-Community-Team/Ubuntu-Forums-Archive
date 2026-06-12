---
title: "Put Ubuntu on an SD card for MAC and enjoy much longer battery life"
date: 2013-09-19
forum: The Cafe
---

### Post by maestrobwh1 on 2013-09-19
Using a MBAir 5,2

Someone was bugging me on why I would bother, and first, because I could and secondly, I am getting the actual 7-8 hours rather than 3-4 using OSX from charge to charge.  It has an SSD anyway so i don't know what OSX does that is eating so much battery.  Even with nothing other than a browser running, the battery gets sucked dry in half the advertised time.

[http://michaelevans.org/blog/2013/01/15/boot-ubuntu-from-an-sd-card-on-your-macbook-air/](http://michaelevans.org/blog/2013/01/15/boot-ubuntu-from-an-sd-card-on-your-macbook-air/)
and
[http://ubuntuforums.org/showthread.php?t=2039799](http://ubuntuforums.org/showthread.php?t=2039799) 

The latter, I just followed the power management tips and the lightnum tip.  The rest works with 12.04.3 pretty well.

and I am using actually a class 10 micro sd card in

[http://theniftyminidrive.com](http://theniftyminidrive.com)

---

### Post by tgalati4 on 2013-09-20
That's impressive performance and it seems that others also get much longer battery life using Ubuntu on a MacAir.  While in OSX, open a terminal and run *top* and see what is running.  You can also install *htop* if you are clever and use that.  My guess is that you have a bunch of cruft that has built up.  After all, you don't own your system, Apple does, so it will do what it wants with your computer, including burning all of your cpu cycles and eating your battery.

My first guess would be the Mac file indexer for spotlight.  It runs constantly going through your disk and indexing files so that you can find stuff in the search bar.  You can probably turn it off, but then it probably breaks stuff in OSX.  The indexers are generally turned off in Ubuntu, until you turn them on.

---

### Post by Bandit on 2013-09-21
My MBA gets 7 hours battery life without any issues. Its a Late 2012 13" model with 256MB SSD and dual core i7. 

Are you sure you haven't changed any of the power management settings around? Or perhaps turned off any services to control CPU throttling? 
It is a curious dilemma.

---

### Post by maestrobwh1 on 2013-09-28
I actually just like Ubuntu better because it allows me to "own" my system.   For example, I have the "up" threshold for the OnDemand govornor in Ubuntu set to 70.  I can't find an app or documentation to even set the CPU in OSX Mt. Lion.  If I did, it would be like $4.99 to $29.99.  MAC software I have found to be somewhat expensive.  I hate Finder as a file browser, so I purchased Path Finder to get some real functionality back.   

I digress.  My power suspicions re OSX:
When I got the MAC air 5,2 I imported a time machine back up from a 2,1 AIR so I suspect that some hidden settings carried over and honestly, it is NOT worth the trade off to start over from scratch to "reinstall" all the stuff I need/want.

I am fairly sure it Firefox is in part responsible, as battery life drops much more quickly when using that when surfing around a lot.

---

