---
title: "web server time freeze and weird load avg data"
date: 2010-08-23
forum: Server Platforms
---

### Post by iMav on 2010-08-23
I am completely stumped.  Found my web server (lighttpd) unresponsive this morning and had to hard cycle it.  After some cleaning up, all was happy.  However, after about an hour of handling a decent amount of web traffic, time freezes as far as the web server is concerned.  I've got an hour of access.log data with the following date:  [23/Aug/2010:20:42:58 -0500]  

It never changes.  The load average now reads 0.00 0.00 0.00 (which is totally inaccurate).  And I am not able to successfully log in remotely.

I have taken the server down 3 or 4 times today and after an hour or so of functioning normally, this is what happens.

Additionally, the local time is now off by 30 minutes.  Trying to force with ntpdate does nothing (or, at the very least, sets it to the same incorrect time)

I am at my wit's end.  Any suggestions?

---

### Post by Vegan on 2010-08-23
Looks like your server has been corrupted.

Check the disk

sudo touch /forcefsck

---

### Post by iMav on 2010-08-23
crazy:

root@runt:/etc# date -s "Tue Aug 24 02:26:12 UTC 2010"
Mon Aug 23 21:26:12 CDT 2010
root@runt:/etc# date
Mon Aug 23 22:09:42 CDT 2010
root@runt:/etc#

---

### Post by craigp84 on 2010-08-24
You're not running ntpd on this box and it's lost its marbles? E.g. in /var/log/messages there's not constant updates from ntpd referring to adjusting the clock?

Assuming that's not the case, i'd be thinking the RTC on the motherboard is up the spout. Rare, but possible.

This is loosing time when it's powered on which is strange, i've seen cases where the box looses time with the power off and that's always presented crazy behaviour when the system's started -- replacement battery for the bios in those cases. But this is different.

---

### Post by iMav on 2010-08-24
ntpd was definitely running.  And working fine until about an hour after the system comes up...then it all goes to heck.

This is a VM, so no motherboard issues (all other VM's and the host OS are fine).

Anyways, I spun up a new VM and am copying my data over.  I'm done banging my head against a wall.  :)

---

