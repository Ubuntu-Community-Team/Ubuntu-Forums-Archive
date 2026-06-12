---
title: "post-start process terminated with status 1..."
date: 2010-02-22
forum: Security
---

### Post by Edict on 2010-02-22
When I restart my computer the following messages come up:
___________________________________________________
init: usplash post-start process (2221) terminated with status 1
* Stopping ClamAV virus database updater freshclan
* Stopping VirtualBox kernel modules
* Stopping the Winbind daemon winbind
* Stopping MySQL database server mysqld
... done
* Shutting down ALSA...
* Asking all remaining processes to terminate
* Deactivating swap...
* Will now restart
____________________________________________________
Is this normal?  I've never seen it before.

---

### Post by cariboo on 2010-02-22
Looks normal to me, it looks like usplash may be broken.

---

### Post by FuturePilot on 2010-02-22
I've seen that before. I think it's just a bug in Usplash.

---

### Post by ericrichards420 on 2010-04-04
Yeah it looks alright, besides usplash. last week I tryed to install a new usplash theme and something went wrong. It wouldn't let me change my theme back like it was. I has to start booting my computer in low graphics mode. after only a couple days of running in the low graphics mode it ruined my video card. it was a 3D graphics card 512 megs of ram. now its in the trash. besure not to run in low graphics mode.

---

### Post by Naggobot on 2010-04-04
I have the same issue. I have never paid much attention to it before now. I run command to terminal

```
ps -A > pslist.txt
```and rebooted. Curiously I was unable to find the reported process number 2298 from the ps -A output list.

Now the next obvious questions are 
1. what is causing this?
2. is there a way or reason to fixit?
3. is this really an issue?
4. does Lucid still run usplash?

---

### Post by cariboo on 2010-04-04
Lucid doesn't use usplash/xsplash, plymouth now gives us the fancy graphic at startup and shutdown. It works for some (me) and doesn't work for others.

---

### Post by gn0m3boy on 2010-12-17
It's possible your kernel needs to be updated - 
reference: [http://ohioloco.ubuntuforums.org/showthread.php?p=8723780](http://ohioloco.ubuntuforums.org/showthread.php?p=8723780)

---

