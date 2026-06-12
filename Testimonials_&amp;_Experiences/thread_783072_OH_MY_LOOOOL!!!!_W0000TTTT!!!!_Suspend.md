---
title: "OH MY LOOOOL!!!! W0000TTTT!!!! Suspend"
date: 2008-05-05
forum: Testimonials &amp; Experiences
---

### Post by artir on 2008-05-05
Ubuntu is just AWESOME (not awesome). I want to express my gratitude to Canonical and the community. With gutsy, suspend& hibernate didnt work on my desktop PC.
But now, they work. and MY PC BOOTS IN 5 SECONDS and I dont need to see the BIOS message... W00t. Kudos to the comunity.

But(there is always a but)
1.The first thing i see after resuming is kinit: no image found and then some lines of debug. Fix= replace with a cool looking bar/grey screen.
2. Network manager is disconnected at beggining, but it auto-connects the wifi past 2 secs. That should be more automatic. 
3. The first time, when i resumed, I were asked for my password.
I entered gconf AKA ubuntu registry and fixed it. I didnt found any GUI to do this. Fix= Add this option to gnome-power-manager.

So im not going to turn my pc off like the old times.
All hail suspend!

---

### Post by artir on 2008-05-05
Edit: I dont have sound after resuming :P

---

### Post by armandh on 2008-05-05
GUI bypass of log on
system/administration/log on screen/tab security/check enable automatic log on /drop down/select name

---

### Post by artir on 2008-05-06
> **armandh said:**
> GUI bypass of log on
system/administration/log on screen/tab security/check enable automatic log on /drop down/select name

I know. I have that enabled. In normal conditions, i dont have to enter my pass, only here.

BTW, the sound issue is progressing quite well on launchpad. Now I have a workareound: sudo /sbin/alsa force-reload

---

