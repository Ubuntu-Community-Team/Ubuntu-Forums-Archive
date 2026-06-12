---
title: "Persistant journal does not rotate"
date: 2017-12-23
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-12-23
I have checked journalctl, and seen that the last 11 days are still logged :confused:  That is way more than the journald.conf settings with its default '1week' :(
Tweaking the values according to the manpage to reduce that unexpected too large history also does not works.

Can someone confirm please, before reporting? (running a gnome on org session)

---

