---
title: "Understanding DD output"
date: 2020-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Sickdove on 2020-04-12
Please forgive me if this is not the right place to post this. The answer probably is short. I am trying to recover an almost(?) dead drive using DD.

I can't decipher the report of the kill command. In the image attached, if I read/understand it correctly, "records in vs. records out" they should match right?

Any insight is much appreciated.

---

### Post by mikewhatever on 2020-04-12
Does it say "Input output error"? If so, the thing is dead

---

### Post by Sickdove on 2020-04-12
> **mikewhatever said:**
> Does it say "Input output error"? If so, the thing is dead

It is dead indeed, hence attempting for 40hrs to save any good sectors using default parameters on a DD terminal. I am just not sure how to read the "Records In/Out" numbers.

356798+68276 records in
425074+0 records out

---

### Post by SeijiSensei on 2020-04-12
I, too, don't know what the X+Y reporting in dd means. I looked at its man page and its info page, and neither explains this output.

Just as a guess the input line might mean that 356798 usable records were read along with another 68276 records that threw errors. 425074 records were written without errors (356798+68276=425074). I'd imagine the 68276 records were replaced with zeroes, but that's also just a guess.

---

### Post by deadflowr on 2020-04-12
Here:
[https://unix.stackexchange.com/questions/238482/what-does-the-two-numbers-mean-respectively-in-dds-ab-records-stats]("https://unix.stackexchange.com/questions/238482/what-does-the-two-numbers-mean-respectively-in-dds-ab-records-stats")

---

### Post by Sickdove on 2020-04-13
> **deadflowr said:**
> Here:
[https://unix.stackexchange.com/questions/238482/what-does-the-two-numbers-mean-respectively-in-dds-ab-records-stats]("https://unix.stackexchange.com/questions/238482/what-does-the-two-numbers-mean-respectively-in-dds-ab-records-stats")

Thank you for the link. Does anybody knows what a, b, c and d represents?. The link explains an experiment using different size blocks to explain something and I didn't get it :(.

a+b records in
c+d records out

The previous post (thank you!) at least takes an educated approach to explain what it might mean. Just not enough to warrant me to cancel 72hrs of salvaging data from a dead drive. (Full disclosure, it's a drive which had a partial backup. So not critical. Attempting to see if i can recover more as a critical drill to know what to do when something goes wrong. Thank you all and stay safe indoors)

---

### Post by SeijiSensei on 2020-04-13
> It means full blocks of that bs size plus extra blocks with size smaller than the bs.

"bs" = blocksize

So the count after the plus sign indicates that 68276 records were shorter than their block size which suggests they are erroneous.

---

### Post by TheFu on 2020-04-13
This is exactly the reason that ddrescue should be used, not dd.
**ddrescue** keeps going when failures happen. It will try to get data from failing sectors multiple times.  The log file will let the command be stopped and restarted later, picking up at the same point.

Hopefully, the OP has decided that having daily, automatic, versioned, backups would be easier and much less stressful than hoping that any data recovery actually works.  Sadly, it took me losing about 80% of my data almost 20 yrs ago before I finally got backup religion.

---

