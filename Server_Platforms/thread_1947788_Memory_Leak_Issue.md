---
title: "Memory Leak Issue"
date: 2012-03-27
forum: Server Platforms
---

### Post by hemi519 on 2012-03-27
Hi All,

I am using ubuntu 10.04 server from one week. I am running a website(PHP,Apache2) with 300 users. Every 15 mins my website will become slow and stops working. After some google search i came to know about memory leak.

I am using a 2GB Ram. Is 2 GB Ram enough for a small website(5000 users). As of now we are having 300 users. 

             total       used       free     shared    buffers     cached
Mem:          2001       1974        26          0          0         19
-/+ buffers/cache:       1874        126
Swap:         4094       1276       2818

Free memory is only 26. If i restart the server it will show 1600 MB and everything works fine for 10-20 mins and then again the problem will repeat.

Can anyone tell me how to solve this issue.

---

### Post by a2j on 2012-03-27
did you make any memory related changes to php and apache config files?

---

### Post by hemi519 on 2012-03-27
> **a2j said:**
> did you make any memory related changes to php and apache config files?

No, I did not do any changes

---

