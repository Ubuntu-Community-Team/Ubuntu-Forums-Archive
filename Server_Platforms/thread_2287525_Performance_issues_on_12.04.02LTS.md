---
title: "Performance issues on 12.04.02LTS"
date: 2015-07-20
forum: Server Platforms
---

### Post by brandon.linden on 2015-07-20
I have 2 mail servers running, both were going very well for a long time (over a year) and I've always kept them updated. Recently In the last week, perhaps 10 days or so, I've been having some issues where services will hang (often mysql) and I have to reboot. I noticed the load averages increasing, after reboot I'll see around 1.5 or so, currently after this weekend, the load on both servers is over 60.

Both these machines are running postfix/dovecot on dell R420 hardware. They are configured separately, they aren't load balancing, they just host different mail services. Running top I don't see anything that sticks out as a particular problem, just looking for suggestions on where to look.

---

### Post by tgalati4 on 2015-07-21
What are the IO WAIT (wa) loads in *top*?  If they are increasing, then it could be a disk drive IO problem.  Also look at *dmesg*.

```
dmesg | more
```
Only post the errors, not the entire output.

---

### Post by brandon.linden on 2015-07-21
So, after sleeping on it, I realized they both shared a common cifs mount. I got in and confirmed that it was inaccessible and causing the load to show high. I restarted the drive and both servers have returned to normal operation.

---

