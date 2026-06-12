---
title: "Reading htop system loads with the i7"
date: 2010-07-07
forum: Server Platforms
---

### Post by R.Bucky on 2010-07-07
I just built a server, which displays 8 cores in the i7 processor. However, because of the 2 threads per core, it shows up as an 8 core system. When viewing htop, it shows system loads at 0.29,0.18, and 0.13 for respective averaging times. How would I calculate actual system load for this processor? Would I divide the average by 4 or 8? Or, is there another method?

[IMG]http://blog.markimoore.com/uploads/i7.png[/IMG]

---

### Post by arrrghhh on 2010-07-07
I believe that's total load average over all the cores... BUT I may be wrong.

---

### Post by R.Bucky on 2010-07-07
I have a hard time believing that an i7 at idle without GUI is operating at 0.13 percent.

---

### Post by arrrghhh on 2010-07-07
From wikipedia:

"For single-CPU systems that are CPU-bound, one can think of load average as a percentage of system utilization during the respective time period. For systems with multiple CPUs, one must divide the number by the number of processors in order to get a comparable percentage."

So it looks like you are correct, just keep in mind that value you're looking at is NOT a percentage.  It's load average.  See the [entire article](http://en.wikipedia.org/wiki/Load_%28computing%29) for some good reading on how load works :D  Very different from utilization!

**I would think dividing by 8 would be proper since the system sees 8 cores...** But, not positive on that either.  Just logical.

---

### Post by R.Bucky on 2010-07-07
Now, the question still remains whether I divide by four or eight, as the true CPU only has 4 cores...

---

### Post by warfacegod on 2010-07-07
Sounds like you have 4 physical cores and with Hyper Threading you also have four Logical cores. Your computer probably won't know the difference and will treat it like 8 cores. So should you.

---

### Post by sh1ny on 2010-07-07
8

---

### Post by R.Bucky on 2010-07-07
8 it is. Thanks

---

