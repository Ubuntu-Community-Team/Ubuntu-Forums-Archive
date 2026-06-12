---
title: "I think I may have been hacked"
date: 2007-09-05
forum: Server Platforms
---

### Post by nemat0de on 2007-09-05
To make  long story short, I am missing a few files and some new ones have been added. Chkrootkit found nothing. 

What should I look for next?

---

### Post by conjur3r on 2007-09-05
Your service's log files would be a good starting point.  Try to determine how they got in, and once found, see what sort of access they gained.  This will give you an indication on the potential damage that was done.  Fingers crossed they didn't obtain root access - in which case it's goooone.

Alot of the time, it is easier to just format/reinstall for peace of mind.  Make sure you backup what you need.

---

### Post by nemat0de on 2007-09-05
I'm rather new at this. What should I be looking for?

---

### Post by lisati on 2007-09-05
It probably won't hurt to check out the protection your router can offer as well.....

---

### Post by Gremlinzzz on 2007-09-05
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by nemat0de on 2007-09-05
Is it odd that my logs only go back about 12 hrs?

The only thing that looks suspicious in in auth.log. I have a bunch of pam_unix authorizations for root coming from cron. Is this abnormal?

---

### Post by conjur3r on 2007-09-05
Are there any archived log files such auth.log.0[.gz] etc?  They may have been rotated.  A clever hacker tries to clean up after themselves by deleting any traces they may have left.

What services have you got running (eg web server, database, ssh, ftp, etc)?

Try other log files in /var/log as well (messages, etc).

---

### Post by nemat0de on 2007-09-05
I checked my archived log files, .1gz, .2.gz. The odd thing is that they are all almost exactly the same. It's as if I have done nothing on my box in the last month. 

Should I post any examples?

---

