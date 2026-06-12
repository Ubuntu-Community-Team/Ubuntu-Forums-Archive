---
title: "bind9 hanging after upgrade (7.04 -&gt; 7.10 -&gt; 8.04)"
date: 2008-08-07
forum: Server Platforms
---

### Post by LodCroppa on 2008-08-07
Hi,

I recently upgraded a busy server that primarily provides mail scanning with amavis/spamassasin/postfix.  I first upgraded from 7.04 to 7.10 using the method described for servers on ubuntu's website ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)), and then immediately on to 8.04 using the same technique.

Things basically went smoothly, but a few hours after the upgrade was complete, bind stopped answering requests.  rndc was unable to communicate with the process as well.  I killed the process, started bind via the init script, and it worked fine for another few hours then hung again.

This has continued for a couple days now.  Sometimes it runs for 12 hours or more, sometimes will die after 10 minutes.  

bind is working as a caching nameserver for localhost only, with authority for a handful of domains used to direct RBL lookups to other local servers.  It does get quite a work out, often doing over 50 queries per second.  

When it dies, it does not exit and does not put anything in any logs that I can find.  I am stumped on how to troubleshoot this further.

Thanks for any assistance

---

### Post by damoxc on 2008-08-07
Have you checked /var/log/daemon.log?

---

### Post by LodCroppa on 2008-08-13
> **damoxc said:**
> Have you checked /var/log/daemon.log?

Yes.  There are normal messages from bind there, but nothing obviously related to the hang / nothing strange right before the hang.  Also checked all other log files for anything strange around the same time, and there just isn't anything odd that I can see.  Load does not exactly correlate with the frequency of the hangs, but may be related, because over the weekend the load is generally lower on that box and the crashes were less often.  Since this hang happens only one or twice on a typical day, its really difficult to be sure of any trends.

---

