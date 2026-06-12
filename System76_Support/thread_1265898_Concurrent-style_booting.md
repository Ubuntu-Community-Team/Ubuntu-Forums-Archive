---
title: "Concurrent-style booting"
date: 2009-09-14
forum: System76 Support
---

### Post by PGScooter on 2009-09-14
Hi,

I found a tip for "making ubuntu faster" and was wondering if it was worth doing on my Pangolin panpv5. Are there any risks/ side effects?

[http://www.ethiopianreview.com/scitech/6044](http://www.ethiopianreview.com/scitech/6044)
> Concurrent-style booting
Turning on concurrency-style booting will allow your dual-core processor (only use this if you have one) to utilize both of its cores while booting. This will make Ubuntu boot much faster. To turn this on, open a terminal and type “sudo nano /etc/init.d/rc”, without the quotation marks. This will open a file and you should scroll down to a line that says “CONCURRENCY=none”. Change this to say “CONCURRENCY=shell”.

Thanks!

---

### Post by thomasaaron on 2009-09-14
Hmmm... Never tried it, but I'd be interested in knowing the result. Be sure to time it before and after.

---

### Post by PGScooter on 2009-09-14
OK, I'll give it a test in the near future. Just wanted to make sure it wasn't a horrible idea to try.

---

### Post by samalex on 2009-09-15
I'd love to see the outcome of this as well...  My boot time on the PanP5 is at about 30 seconds or less which is awesome in of itself, but to shave some more even off this would rock.

Thanks --

Sam

---

### Post by samalex on 2009-09-15
Hello again,

I wanted to test his on my PanP5 system, but before doing it I did some research and found setting 'CONCURRENCY=shell' in the init.d/rc can cause some problems.  

Also I found [this post]("http://cyounkins.blogspot.com/2008/12/supposed-ubuntu-speedups.html") where someone tried these updates but didn't see any significant increase in speed.

I've wanted to update grub to decrease the countdown there, but outside of that I'll probably just stick with the process I have now which is already impressive.  Heck my work PC, which is supposed to be 'latest and greatest' as of a year ago takes a few minutes to boot, and even then after logging in it takes another 1-2 minutes for virus scanner and all the other pre-installed apps on our network to start.  So my 30 seconds from power button to joy on the PanP5 isn't anything to harp about I guess.

Sam

---

