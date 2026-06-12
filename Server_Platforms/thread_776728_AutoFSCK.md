---
title: "AutoFSCK"
date: 2008-04-30
forum: Server Platforms
---

### Post by expatCM on 2008-04-30
On the desktop edition you can install AutoFsck 
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)
to run the periodic fsck when the system powers down rather than facing the delay or running when you power on.

This utility is really very good but it depends on a gui.

Is there any way of accomplishing the same for the server edition?

---

### Post by musther on 2008-05-01
I've been talking to expatCM via email about this, and have thrown together a server 'shutdown call' version of autofsck for him, you can find it here for now:
[https://wiki.ubuntu.com/AutoFsck?action=AttachFile&do=get&target=autofsck-server-1](https://wiki.ubuntu.com/AutoFsck?action=AttachFile&do=get&target=autofsck-server-1)

This version is designed for people who have servers, perhaps home servers, which they do not leave on all the time, maybe they're shut down overnight by a cron job.

Download this file, rename it to whatever you want, make sure it's executable, and put it somewhere convenient.  

When you want to shut down your server, simply call this script (or get cron to do it for you).  

I'm looking into incorporating this into AutoFsck, or simply making an AutoFsckServer edition, we'll see.

For now, I hope this helps.

---

### Post by expatCM on 2008-05-01
This really is excellent and has exactly solved my need.

Thank you very much indeed for this and in such a fast response time.

I look forward to seeing formal release of the Server Edition ...  :)

---

### Post by stronzo on 2009-03-28
Thanks for the script.
But there seems to be a big bug!
It checks my filesystem after a reboot EVERYTIME i shut down the machine, insted of every 30th time. can someone see the bug in the script??
i couldnt find it. please help me, this would be so useful

---

### Post by stronzo on 2009-03-29
push

---

### Post by musther on 2009-07-13
Is this still a problem for you?

---

