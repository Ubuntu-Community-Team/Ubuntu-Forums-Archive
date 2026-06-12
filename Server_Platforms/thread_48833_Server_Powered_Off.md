---
title: "Server Powered Off"
date: 2005-07-14
forum: Server Platforms
---

### Post by mdr on 2005-07-14
hmmm
just wondering if anyone has any ideas to this hoary problem.
Been running a Ubuntu Hoary Server (mainly for Samba) for my company for the last few months - say 5 - no issues.

Until this week.  Each morning the server has been turned off early in the morning but with no error messages, nothing in logs that I can see.
Switch back on and all is ok.

Not human interference as there is no access as the PC is in a locked room.

The only thing I can think of is the box shutting down due to overheating.  Just surprising that this is happening after a few months where operation is fine.

Btw the server box is an Antec 4U Rack Server Case so cooling and PSU should be fine.

---

### Post by LordHunter317 on 2005-07-14
If it's in a full rack, then no, cooling may not be fine.

Run sensorsd and get monitoring on the box.

And are the shutdowns occuring at the same time?  IF so, odds are very high it's due to a cron job causing trouble or an ordered shutdown.

---

### Post by mdr on 2005-07-18
yep it seems to have been a cron job.
the symlink I put in to cron.daily did not have sufficent +x rights (sigh)

Not sure why this would power off the server though.
anyways thanks for the pointers.

---

