---
title: "How much CPU % is my Server Using?"
date: 2009-07-02
forum: Server Platforms
---

### Post by supanatral on 2009-07-02
My Macbook Pro has two cores, so when I look at activity monitor, 100% CPU means I only have one core maxed (or 200% if I have both maxed). This is why my question arises.

The Ubuntu Server I'm managing has 2 x Intel Core 2 Duo processors so in total, it has 4 cores. When I use the "top" command, does 100% mean I have all four cores max or just one?

---

### Post by Boondoklife on 2009-07-02
while in top press 1

also if you press ? it will give you all kinds of good info

---

### Post by supanatral on 2009-07-02
Ok, so it looks like we aren't maxed which is good! Here's my CPU usages:

> Cpu0  :  1.5%us, 22.6%sy,  0.0%ni, 15.2%id, 59.4%wa,  0.3%hi,  0.9%si,  0.0%st
Cpu1  :  0.6%us, 17.4%sy,  0.0%ni, 39.0%id, 41.3%wa,  0.6%hi,  1.0%si,  0.0%st
Cpu2  :  2.2%us, 15.0%sy,  0.0%ni, 35.0%id, 46.5%wa,  0.0%hi,  1.3%si,  0.0%st
Cpu3  :  0.9%us,  6.9%sy,  0.0%ni, 48.8%id, 42.8%wa,  0.0%hi,  0.6%si,  0.0%st


So, there's quite a bit idle...but if that's the case, then why are my load averages high?

> root@Hypervisor:~# w
 14:41:24 up 1 day, 16:49,  2 users,  load average: 10.25, 9.52, 10.61


Could that be from the hard drives not being able to keep up?

---

### Post by ian dobson on 2009-07-02
Hi,

Looks as if you I/O system can't keep up (20% system, 50% wait).

Try iotop and iostat to see how hard the I/O is being hit.  How much ram do you have in the box? Do a free to see how much swap is being used.

Regards
Ian Dobson

---

