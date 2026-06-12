---
title: "Apache2 fails to start"
date: 2008-05-29
forum: Server Platforms
---

### Post by satimis on 2008-05-29
Hi folks,


Ubuntu 6.05 drake amd64


$ sudo /etc/init.d/saslauthd start```

Password:
Starting SASL Authentication Daemon: (failed).

```


$ tail /var/log/daemon.log```

May 30 00:00:01 lampserver squid[4311]:         0 Objects expired. 
May 30 00:00:01 lampserver squid[4311]:         0 Objects cancelled. 
May 30 00:00:01 lampserver squid[4311]:         0 Duplicate URLs purged. 
May 30 00:00:01 lampserver squid[4311]:         0 Swapfile clashes avoided. 
May 30 00:00:01 lampserver squid[4311]:   Took 0.7 seconds (   0.0 objects/sec). 
May 30 00:00:01 lampserver squid[4311]: Beginning Validation Procedure 
May 30 00:00:01 lampserver squid[4311]:   Completed Validation Procedure 
May 30 00:00:01 lampserver squid[4311]:   Validated 0 Entries 
May 30 00:00:01 lampserver squid[4311]:   store_swap_size = 0k 
May 30 00:00:01 lampserver squid[4311]: storeLateRelease: released 0 objects 

```
Please advise where shall I check and how to fix the problem.


TIA


B.R.
satimis

---

### Post by azadpanchi on 2008-07-25
I am not sure I understand how this issue is related to apache failing.  Possible for you to provide additional information for your setup and steps to recreate the issue.

---

### Post by satimis on 2008-07-25
> **azadpanchi said:**
> I am not sure I understand how this issue is related to apache failing.  Possible for you to provide additional information for your setup and steps to recreate the issue.
Hi azadpanchi,


Thanks for your response.


Problem solved already.  It was the problem on Cyrus.


B.R.
satimis

---

