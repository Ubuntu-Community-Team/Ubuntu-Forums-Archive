---
title: "firestarter starts with Gutsy?"
date: 2007-10-24
forum: Server Platforms
---

### Post by isileth on 2007-10-24
I've  just upgraded my system to Gutsy with a clean reinstall.
I then installed Firestarter and used the wizard.
Everything seemed just fine, but when I was watching the boot process I noticed that I read
firestarter stopped yes
firestarter started yes
after a while it read
stars firestaster failed
I'm not used to have the icon to show firestarter's work, but I never had one before.
If I look at the processes in system monitor, Firestarter doesn't seem to be there, but if I go to System - Administration, it seems up and running.
What could this be?
Am I paranoid or what?

---

### Post by steve909 on 2007-10-24
I have also just done a fresh install, as my upgrade seemed to cause firestarter to quit for no reason.
However, even after a fresh install and download of firestarter, firestarter still quits.
I've checked using ps aux grep | firestarter and it is not running. But I can't remember where this would be logged. Can anyone give us any clues?

Thanks in advance.

---

### Post by gmc on 2007-10-25
```

root@mobile:/home/g# firestarter 

(firestarter:12907): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Firewall started

[B]***MEMORY-ERROR***: firestarter[12907]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)
[/B]
```
Here's what I've discovered. I get the message in **bold** after a few minutes of watching the gui log rejected connections. I have no idea what is causing the problem though.

Gord

---

### Post by indosupremacy on 2007-10-25
the same problem happen to me too
any suggest please?
thank u

---

### Post by erginemr on 2007-10-25
AFAIK, Firestarter is just a frontend to a text-mode firewall, IPTables, which is already installed in Ubuntu but not active by default. Firestarter just activates it and stops. That's why, you do not see it run all the time, by when you run its dialog, it reports the firewall as running OK.

There is an easy way to check whether you are behind a firewall or not. The 1Shields Up!" site is reknown for thier safety checks. It web address is:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

There I had run the test before installing Firestarter and it had reported all my ports as "closed". Then, I installed Firestarter, rebooted, and re-visited the site (without Firestarter running). The same test reported the available ports as "stealth" this time, which is much better of course.

---

### Post by indosupremacy on 2007-10-26
> **erginemr said:**
> AFAIK, Firestarter is just a frontend to a text-mode firewall, IPTables, which is already installed in Ubuntu but not active by default. Firestarter just activates it and stops. That's why, you do not see it run all the time, by when you run its dialog, it reports the firewall as running OK.

There is an easy way to check whether you are behind a firewall or not. The 1Shields Up!" site is reknown for thier safety checks. It web address is:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

There I had run the test before installing Firestarter and it had reported all my ports as "closed". Then, I installed Firestarter, rebooted, and re-visited the site (without Firestarter running). The same test reported the available ports as "stealth" this time, which is much better of course.

thanks bro...it make me feel more secure....
:)

---

