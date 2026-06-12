---
title: "/var/lib/dpkg/lock"
date: 2016-12-23
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2016-12-23
Every time I do updates I have to delete the lock two times before it will do the updates ?

Anything I can do to fix that ?

Thanks

---

### Post by dino99 on 2016-12-23
Did you have made some tweaks being root ? Maybe test a new user profile.
[http://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/](http://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/)

---

### Post by zika on 2016-12-23
Check if You have unattended-upgrades running behind the scene...
Be sure that You have only one apt process active...
...

---

### Post by cecilpierce on 2016-12-23
Thanks guys.

---

### Post by seeker5528 on 2016-12-23
First,

Under 'System Settings --> Software & updates', one of the tabs will have an option about how often to check for updates.
I recently had to set the option to never check after not having any issue with it for quite some time, so don't know what changed, but that was the final piece that got rud of the messages about lock files.
You should not have to delete these locks, it should only be some number of minutes after boot/login that these files are locked while the list of available software is being updates.

If that doesn't take care of it, then you have to look at the things that are in the autostart.

Look for update notifier, gnome software, ubuntu software, etc.... in 'startup applications', if you find that on your system. I have a mixed system so am not %100 sure startup applications is part of the stock Ubuntu anymore. Looks like 'Startup Applications' is provide by 'gnome-session-properties', if you are looking for the command to type in. 

It used to show up in 'System Settings', but not showing there on my system currently, I had to click on the 'HUD' and search for 'startup' and it was shown to me in the results.

If I search in the HUD for 'session' I also get a 'Desktop Session Settings' which looks to be provided by lxsession-edit, which is provided in it's own package, looks to have a more inclusive list of things to start/or not start. And less dependncies if you don't have another session editor installed already.

My issue with it is, since I prefer Synaptic for managing installed software, when the list of software is updated outside of Synaptic, Synaptic doesn't alway know what is new on the list.

Later, Seeker

---

### Post by seeker5528 on 2016-12-23
Looks like the thread was marked solved while I was looking at things on my system and composing my reply.

---

### Post by cecilpierce on 2016-12-24
@Seeker

     Seems its not solved, still got the lock.
I tried never in updates and looked in autostart still have the lock.

Thanks

---

### Post by zika on 2016-12-24
```
:~$ sudo systemctl status unattended-upgrades.service
&#9679; unattended-upgrades.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
```Of course, You could leave it active but, then, You should just wait untill it finishes its first run after boot, (almost) every boot... ;)

---

