---
title: "ltsp: heavy sporadic kernel cpu usage"
date: 2011-08-01
forum: Server Platforms
---

### Post by markandrews on 2011-08-01
Hello,
A few weeks ago, I made an ltsp server on core i7 running ubuntu 10:10.
Most things are fine (though I have a few small issues), except I have a major problem with sporadic intense kernel cpu usage. Watching htop, every few hours, all 8 cores blast at nearly 100% for about 5 minutes, and then they drop off to zero. In that meantime, I can barely type a single character into a terminal. There is no process per se doing this. The activity as reported by any system monitor I use shows it to be the kernel (the bars in htop are red, not green, for example). 
I have been baffled by this, but have to get to the bottom of it. I have spent the last few weeks googling, and talking on forums (I mean, fora), to no avail. My next step will be to re-install everything. 
My question for this forum is, has anyone else noticed anything like this on an ltsp system on ubuntu? If not, then it must be some peculiarity to my setup. I just thought I would inquire in case I am not alone?
many thanks
-m
p.s. I am not totally certain that this is an ltsp issue. It just began at the same time as when I set up ltsp. I had been using the server happily as a desktop for about 18 months.

---

### Post by meadmarc on 2012-01-27
How many machines?

I am having similar problems in my daughter's school.  Usually happens when I am at my day job, but once I got to see it in person when there was only one user logged in after school!

Two dual core processors running at 3.06 maxed out completely.

Fans screaming for air.  Quite dramatic.

Does not seem to be related to how many users are on line, can't seem to find a pattern.

---

### Post by Wayne_V on 2012-01-28
top should show what process is using cpu.  just make sure you are sorting by cpu usage.

you could also turn sadc on (see /etc/default/systat).   May want to add "-S ALL" option until you figure out what is going on.  see 'man sar' and 'man sadc'

---

