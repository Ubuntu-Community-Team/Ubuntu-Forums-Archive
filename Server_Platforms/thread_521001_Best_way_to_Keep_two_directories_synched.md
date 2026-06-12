---
title: "Best way to Keep two directories synched????"
date: 2007-08-08
forum: Server Platforms
---

### Post by yebo29 on 2007-08-08
I'm running low on options here....

I have two servers, and each of these servers has a directory I want to remain synched.

One of those servers I want to keep off most of the time (don't want my electrical bill in th sky, and I don't need it on all the time), but when I do need it on, I want it to sync that directory with the other server that does remain on at all times.

I can use nfs, smb.... anything! I just can't find something that I can run at boot time or through cron! 

Thanks whoever helps!

PS: I know of the existence of rsync, but can't seem to get it to work the way I need it...... If perhaps someone could point to a tutorial to keep two directories in sync using this algorithm.......

---

### Post by foxylad on 2007-08-08
You definately want rsync - persevere with google for help. You can then add a the rsync command to /etc/if-up.d on the usually-off machine, and it will kick off whenever you start it.

---

### Post by yebo29 on 2007-08-08
Interesting....

So on if-up.d I just add my rsync command and when that if comes up it will run that command??

That'd be sweet!

---

