---
title: "only the first user to log in has audio"
date: 2012-02-05
forum: Ubuntu Studio
---

### Post by amirbd89 on 2012-02-05
Hello,
I've recently upgraded my ubuntu 11.10 to ubuntu studio 11.10 using this guide: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

and since then, only the first user that logs in after a reboot has audio...
I'm using ESI Juli@ sound card which worked great before.

When I go to sound settings I can see under 'hardware' that there's a device missing for all the users who logged in later(Envy 24). 

I'm quite a newbie so I don't really know how to check things farther...
Does anyone have an idea what has gone wrong with my upgrade and how can I fix it?

---

### Post by amirbd89 on 2012-02-05
a short update:
when I run 
sudo alsa force-reload
the current user that is logged in gets sound and the missing device, but than the device disappears for all the other users...

---

### Post by CivilizationII on 2012-02-17
> **amirbd89 said:**
> a short update:
when I run 
sudo alsa force-reload
the current user that is logged in gets sound and the missing device, but than the device disappears for all the other users...


Verify also your additional users belonging to audio group

---

