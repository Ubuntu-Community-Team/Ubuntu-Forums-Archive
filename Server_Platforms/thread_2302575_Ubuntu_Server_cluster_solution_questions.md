---
title: "Ubuntu Server cluster solution questions"
date: 2015-11-11
forum: Server Platforms
---

### Post by Phil_Kelly on 2015-11-11
Hello:

Looking for some direction to create a solution to the following:

Use 2 beefy servers running Ubuntu Server..and running one Windows virtual machine that runs an application.   Server A is primary, and server B is standby.  If server A fails....needs a reboot...etc, server B automatically fails over, and becomes primary, and then server A becomes the standby.  Meanwhile, the Windows VM runs and the users of the VM notice no issue with the instance of Windows.   

Avance has a solution like this...I believe running either Red Hat or Fedora...but it is stupid expensive.  

Anyone know of a similar situation running with Ubuntu Server?  The bottom line is the Windows VM.  This would have to be a mission critical VM that would run regardless of which server is primary.

I am not looking at load balancing, just machine redundancy.

Any input would be appreciated.

Best,

PK

---

### Post by TheFu on 2015-11-11
I've never tried it on Ubuntu  (or any Linux), but  ....
[https://serverfault.com/questions/90378/ubuntu-clustered-kvms](https://serverfault.com/questions/90378/ubuntu-clustered-kvms)

* Shared storage or replicated block storage.
* heartbeat to track failures - kick off some shell scripts.
* some shell scripts to bring 1 OS down and the other one up.

Clustering seems to be used much more often on RHEL than Ubuntu.  Might be worth going that direction if you don't have much clustering hands-on experience.

If possible, be better off going with a load-balanced solution, IMHO, but not all applications are architected in that way.

BTW, in a prior life, I designed and deployed some fairly large clusters, but we tried to avoid active/failover unless that was the only possible solution.  Usually just the DBMS. We used VCS on HP-UX, AIX, and Solaris.

---

### Post by Phil_Kelly on 2015-11-22
Sorry for the late reply...3 weeks on the road...had to go off the grid a while

Thanks for the info.  Might try some experimentation.  Might see if I can requisition a couple machines from work in Dec to experiment.

PK

---

