---
title: "viewing snort log"
date: 2015-02-15
forum: Security
---

### Post by sniper8752 on 2015-02-15
I am trying to view the snort log.  It has special characters, then host/cache-control,location, etc.  I tried to run this command: snort -dv -r ./snort.log.  But I get this error:
Can't initialize DAQ pcap (-1) - uknown file format.

Any help is much appreciated!

---

### Post by KenF on 2015-05-22
> **sniper8752 said:**
> I am trying to view the snort log.  It has special characters, then host/cache-control,location, etc.  I tried to run this command: snort -dv -r ./snort.log.  But I get this error:
Can't initialize DAQ pcap (-1) - uknown file format.

Any help is much appreciated!


I just recently installed snort as well.  Same problem here.

It appears that the format is unified2 (or u2).  According to the snort documentation, one should be able to view this using u2spewfoo (or translate to a different format with u2boat).  Unfortunately these don't appear to be packaged by Ubuntu 14.04.  I found this bug ( [https://bugs.launchpad.net/ubuntu/+source/snort/+bug/1246952](https://bugs.launchpad.net/ubuntu/+source/snort/+bug/1246952) ) indicating that these should have been packaged, but it looks like there hasn't been any activity (listed in 2013).

Can't help much more than that ... but I'll likely compile/install those myself.

---

