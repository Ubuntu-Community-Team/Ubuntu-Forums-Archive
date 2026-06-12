---
title: "Firestarter Daemon?"
date: 2006-11-07
forum: Server Platforms
---

### Post by FeraTech on 2006-11-07
I'm having problems with firestarter. Is there a way to create a script which will restart it every 30 min or start it up if it isn't running?

Firestarter keeps closing on me. Then if it's been running for a while it will simply stop working and the blocked IPs will stop refreshing. I've tried reinstalling it several times with the same results.

---

### Post by woedend on 2006-11-07
you could try doing this with a cronjob.
open an empty text file, make it say something like this

00 * * * * /etc/init.d/firestarter restart
30 * * * * /etc/init.d/firestarter restart

then save into your home directory as a file called whatever, lets say cronjob1.
open a terminal, and simply type
sudo crontab cronjob1
this will set it to automatically restart at 00 and 30 min of every hour.
sudo must be used since only root can restart it, and this must only be done once, as cronjobs are saved permanently until deleted.

---

### Post by woedend on 2006-11-08
if you are on edgy...i just read about ubuntu using event.d now.  Is firestarter now placed there(i havent used ubuntu in a while)?
if so(and the command sudo /etc/init.d/firestarter restart throws an error),try sudo /etc/event.d/firestarter restart  instead and if it works, replace where applicable above.
if on dapper or before, should be fine as written above.

---

