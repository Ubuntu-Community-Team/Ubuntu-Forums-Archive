---
title: "command plugin"
date: 2012-08-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-08-30
With the move to gsettings getting the command plugin working seems to be a bit of a circular deal here. Don't know if anyone has found it easier.
On a newer install setting a command in ccsm fails, as soon as the plugin window is closed the command disappears. 
Setting directly in dconf also seems to not work until 'command' shows up in the unity section (org.compiz.profiles.unity.plugins, screen 2
(also command 0 in ccsm is command 1 in dconf..
So going back & forth somehow gets it enabled eventually.

Another current issue is the corner edge binding, while not a conflict with the L or R edge bindings for 'flip' (wall or rotate),  will somehow be seen as such after a reboot & no longer work.
The workaround for the moment is to disable the flip binding in wall or rotate

---

