---
title: "Ubuntu server 12.04 drive configuration"
date: 2012-08-28
forum: Server Platforms
---

### Post by bbabr on 2012-08-28
Hello,

We have a new server having the following drive arrays:

2 x 146GB drives in RAID 1
4 x 300GB drives in RAID 5

We are going to install Ubuntu server 12.04 (x64) which will be a database server (PostgreSQL). What is the best practice hard drive configuration we should implement?

Thanks.

---

### Post by wirelessmonkey on 2012-08-28
Are the drives SAS? What are your PostgreS DB size expectations?

Hardware or Software RAID on both?

---

### Post by bbabr on 2012-08-28
The drives are SAS drives and it's a hardware RAID on both arrays.

DB size can be as large as 50GB-100GB.

Thanks.

---

### Post by wirelessmonkey on 2012-08-29
Ok, so with a DB of that size, and assuming you are backing it up to a separate location, I would suggest doing a raid 10 instead of 5 unless your DB transaction load is very light. 

With a RAID 10 you will have ~600GB, with much faster throughput. You will still be able to lose a drive, and you won't have to be concerned with parity calculation overhead.

A RAID 5, you will have ~900GB, but arguably about 1/2 of the IOPS of RAID 10 due to parity overhead.

Since your arrays are comparatively small, you will of course want to decide between space and performance, depending on your requirements.

Best of luck!

---

### Post by bbabr on 2012-09-04
Thank you for your advice. I went with RAID 10 (as you suggested).

---

