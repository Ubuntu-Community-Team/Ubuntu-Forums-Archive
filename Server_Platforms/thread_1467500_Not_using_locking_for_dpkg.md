---
title: "Not using locking for dpkg"
date: 2010-04-30
forum: Server Platforms
---

### Post by Spiritof76 on 2010-04-30
Help I went to upgrade my server system to 10.4, I had a power failure over night. WEhen I went to do the the upgrade I get.
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Typing in sudo dpkg -- configure -a 
gives me:
dpkg: unable to access dpkg status area: Read-only file system

Can I salvage this ?

---

### Post by Spiritof76 on 2010-04-30
Well I still don't know the proper way to have fixed this, but I shut the system down and rebooted.. The system came up with a whole bunch of errors.  but when it finally stopped I rebooted again and the system came up some what clean. did an apt-get update then apt-get upgrade and all seems well.

---

