---
title: "Server 17.04 requiring iSCSI on install"
date: 2017-09-12
forum: Server Platforms
---

### Post by bcdennis on 2017-09-12
I'm trying to install Server 17.04 but when I get to the disk partitioning part, it's prompting me to configure it via iSCSI.  I do not have this setup, nor intend to, nor are provided any other options to partition during the setup process.  How do I get it to install it normally?  I can install desktop just fine.  Just not server.

I'm doing this off a bootable USB.

---

### Post by TheFu on 2017-09-14
This won't help with 17.04. Sorry.

In general, running Ubuntu Server should only use LTS releases.  17.04 support ends in 3 months, making that install less than useful, IMHO.  17.10 has a similar issue.  16.04 is still the most recent LTS available.  I have only one 16.04 server. All the others are still on 14.04.  New is the enemy of stable.

That 16.04 system does have iSCSI client installed and there are 2 processes running.  
```
$ sudo  update-rc.d  iscsid disable

``` should fix my issue, but it won't help you. Sorry.

The main reasons to run a non-LTS server are:
1) testing to report issues (like this) to a bug tracker
2) having hardware so new that the LTS release with the newest kernel won't work.  There was a time when Ryzen needed that, a 4.11+ kernel is helpful.

Besides those reasons, stay LTS.

IMHO.

---

