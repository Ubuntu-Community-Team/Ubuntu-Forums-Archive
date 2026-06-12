---
title: "Server?"
date: 2011-11-16
forum: Server Platforms
---

### Post by andrea000 on 2011-11-16
I'M setting up a server on a friends PC.As a file server goes what would you go with?He is using a 8 year old HP PC and only has 128 mb of ram.I suggested he went with freenas 8 but i was wondering if there was a Linux server that would have and let him add more features if he wanted them?

---

### Post by lisati on 2011-11-16
My $0.02: If you're looking at putting Ubuntu Server on the machine, and possibly some other distros, a bit more RAM probably would probably be a good thing.

---

### Post by andrea000 on 2011-11-16
> **lisati said:**
> My $0.02: If you're looking at putting Ubuntu Server on the machine, and possibly some other distros, a bit more RAM probably would probably be a good thing.

I know Ubuntu server wouldn't work on it and he has done told me that he didn't want to spend anything on doing this I'M just trying to get the best server OS that will work on his old PC.He has just upgraded to a new PC and i told him he didn't need to toss his old one out just yet.So what do you think freenas?

---

### Post by lisati on 2011-11-16
My experience of administering a server is limited to Ubuntu, so I'll have to defer to the wisdom of others about other distros to investigate.

---

### Post by rubylaser on 2011-11-16
FreeNAS will work fine, although, I'd still use version 7 as version 8 is a complete rewrite and does not contain the same feature set at this point.  

Personally, I'd try to upgrade the machine to at least 512MB, and then I'd just install a base Debian Lenny(5) or Squeeze(6) install on it.  At 256 MB of RAM, Debian will work just fine too.

The benefit of going with FreeNAS is it comes with a nice web interface out of the box, and if you want a storage server and support for storage related services, it really doesn't get much easier to setup.

---

### Post by drdos2006 on 2011-11-16
Lubuntu will run on 128 Meg of RAM

[http://lubuntu.net/news](http://lubuntu.net/news)

> 
lubuntu is targeted at "normal" PC users running on low-spec hardware. Julien Lavergne, head of development from France, says: "lubuntu users may not know how to use command line tools, and in most cases they just don't have enough resources for all the bells and whistles of the 'full-featured' mainstream distributions".

The first official version of lubuntu is released as a "stable beta" marking lubuntu as a usable system that is yet undergoing continuous improvements to enhance user experience and speed. Minimum requirements for lubuntu are comparable to Pentium II or Celeron systems with a 128 Mb RAM configuration, which may yield a slow yet usable system with lubuntu. Mario Behling, founder of the project from Berlin says: "It should be possible to install and run lubuntu with less than 128 Mb memory. For browsing the Internet without flash 64 Mb RAM is probably enough on some machines, but for other applications the speed may not be suitable for practical use."


regards

---

### Post by Doug S on 2011-11-16
For what its worth, right now I am running Ubuntu Server edition 11.10 on a 15 year old 200 Mhz computer with 128 Megabytes of memory. I use the computer just as a test computer. I only upgraded from Ubuntu server version 6.06, that had been running on it for several years for these reasons: To see if it could be done; So that my test machine would be a little more current; And so that I could claim to have the most pathetic 11.10 server.
I am not claiming that it works very well, but it is working, albeit ssslllooowwwlllyyy.
Installation was pretty slow also.
This computer is not a router, nor do I have samba running on it.

---

### Post by andrea000 on 2011-11-17
Thanks for the help everyone.Here is what I'M going to try.

Frist I'M going to try ubuntu server if i have problems with that one I'LL try Lbuntu if that one doesn't work I'm going to try VectorLinux Light Edition and if i have problems with that one the last one I'M going to try is freenas.I was going to try freenas to start with but from what i understand it needs to run off a flash drive so the hard disk is free for storage I may be wrong on this and if i am please let me know but he has a big hard disk so space isn't a problem.
Thanks

---

