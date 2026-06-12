---
title: "Server is slow after upgrade to 10.04.1 LTS"
date: 2010-12-31
forum: Server Platforms
---

### Post by tuaris on 2010-12-31
About 3 months ago I upgraded from 8.04 to 10.04 and the experience has since been very problematic in regards to overall performance.  The problem is mostly with MySQL, but I have also noticed that the smallest amount of disk IO slows down the system a lot.

I was expecting a slight performance improvement before I upgraded, but instead I got a very big opposite.  I tried tweaking the MySQL server settings, but the improvement has been minimal.

At this point I am going to have to make a new system with something like Centos (I've heard good things about it's performance).  

Before I do, I want to give Ubuntu one last chance and ask if anyone knows anything that can be done to fix the performance issues.  At the very least go back to something that is comparable to 8.04?

---

### Post by virtuoosi on 2010-12-31
> I upgraded from 8.04 to 10.04

Did you do a clean install or did you upgrade?

---

### Post by tuaris on 2011-03-26
This was an upgrade.

I did a test with FreeBSD 8.1 on the same hardware and the difference in performance is like night and day (even better than before I upgraded).  This almost makes me want to cry for joy and temps me to switch my hosting platform to BSD.

I already tried optimizing the mysql.conf with very little improvement.

---

