---
title: "AVG not updating"
date: 2006-10-30
forum: Server Platforms
---

### Post by eilu on 2006-10-30
AVG anti-virus ios no longer updating. The AVG updater crashes (or seems to- it asks for the root password but nothing happens) and the update button in AVG itself displays an error that "avgupdate is already running" even if it is not. I've done this on a fresh boot and I checked the ssytem monitor to be sure.

Problem started when I had to force the updater to end two nights ago because I had to get offline, and it hasn't worked since. Any ideas?

---

### Post by Sef on 2006-10-30
Have you tried to uninstall then reinstall AVG?

---

### Post by eilu on 2006-10-30
no, not yet. how do I uninstall in terminal? Sorry, I'm a bit new to this.

---

### Post by rlozano on 2006-10-31
the AVG update should go with a root authority, i believe.

---

### Post by eilu on 2006-10-31
> **rlozano said:**
> the AVG update should go with a root authority, i believe.

yes, AVG runs as root.

---

### Post by Bill H on 2006-12-01
It occurres because the update agent died half way through an update. The lock file that tells it if it is still running was left behind. The solution for this is delete avgupdate.pid lock file

sudo rm -r /opt/grisoft/avg7/var/run/avgupdate.pid

If you don’t have this file, then try doing a search using 

locate avgupdate.pid 

Check this Website for usfull tips: 

[http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html#comment-805](http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html#comment-805)

---

### Post by shaggly on 2007-01-02
Thanks Bill, you're a lifesaver.

I've been scratching my head for the last 1/2 hour trying to force the updater to start again, trying all kinds of insane file moving, etc etc.

If only I wasn't running a dual boot system, then I wouldn't feel the need to bother with this silly AV scenario. ](*,) ](*,) :evil:

---

