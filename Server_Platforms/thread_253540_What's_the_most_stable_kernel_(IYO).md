---
title: "What's the most stable kernel? (IYO)"
date: 2006-09-08
forum: Server Platforms
---

### Post by JLTB on 2006-09-08
Hey,

I'm runnning **2.6.15-26-amd64-xeon** on my Ubuntu server and having more hic-ups than I'm used to.  Everything from apache child processes seg faulting randomly to mysql corruptions to strange race conditions.

Would switching to the amd64-generic kernel help?

What kernel version(s) are you running?  What's working well for you?

_Our hardware:_
Dell 2850 PowerEdge
Dual Xeon 3.0 GHz with HT (4 "cores" total is how linux sees it)
64bit Ubuntu 6.06 Server install
4 GB Ram
600 GB HD space in RAID 10 SCSI

_What we do_
Running a LAMP stack for a high availability website, with LOTS of uploads and downloads (it's an indie music site).

_Other versions.._
PHP 5.0.5 (from breezy, the dapper packages, 5.1.2, butt heads with APC)
Mysql 5.0.something

Thanks!!

---

### Post by Uluen on 2006-09-09
I'm running two machines with **2.6.15-26-k7 #1 SMP PREEMPT**, no problems at all.
Do you need 64bit? I see you only have 4GB RAM. 
Tried disabling HT? IIRC the benefits for most servers is null.
Did you run Memtest for atleast 24 hours?

---

