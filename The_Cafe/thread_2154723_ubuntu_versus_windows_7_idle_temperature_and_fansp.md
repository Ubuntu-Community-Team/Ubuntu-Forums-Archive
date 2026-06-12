---
title: "ubuntu versus windows 7 idle temperature and fanspeed"
date: 2013-06-15
forum: The Cafe
---

### Post by rrich1974 on 2013-06-15
i challenge you guys to do some testing. if you have a dual boot machine (ubuntu/w7) i would like to test what is the temperature and the speedfan. 
on my machine:
wind 7: around 42C and 2500 rpm (sometimes 0)
ubuntu: around 42C and 3000 rpm (never 0) 

Later Edit: it seems that the fanspeed goes down to 2500 rpm after all (on ubuntu) but still never stops! 

what do you think?

---

### Post by abhich on 2013-06-17
looks good ..
for me 
ubuntu ~50 
win 7 ~45

for me the fan is not much of a issue ... super quiet in both the OS

---

### Post by Cheesemill on 2013-06-17
Both OS's

Fan speed 1200
Temp 38°C

This machine is always folding so at 100% CPU. If I let it idle this drops to around 800RPM and 21°C on both.

i3-530 overclocked to 3.7GHz

---

### Post by rrich1974 on 2013-06-18
> **abhich said:**
> looks good ..
for me 
ubuntu ~50 
win 7 ~45

for me the fan is not much of a issue ... super quiet in both the OS

and don't you think there is a big difference? in my opinion, it is! how is your idle CPU load? it must be 0-1%. 
if you have the same load as windows, it seems that the linux is not quite fit for your hardware. maybe you can try another kernel...

---

### Post by rrich1974 on 2013-07-19
back again!
after some researches, i have found that setting the radeon driver to LOW power state, decrease the power consumption with about 2 W. i followed this link: 
 [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI)
what it is pretty strange is that playing a 1080p video not seems to be affected. 
keep in mind, i am talking about an old x1270 mobility radeon. 
it would be nice to have a GUI for changing the power state of video card....some kind of "open catalyst contol center".

---

