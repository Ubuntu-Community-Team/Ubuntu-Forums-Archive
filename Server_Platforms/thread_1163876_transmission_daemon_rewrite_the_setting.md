---
title: "transmission daemon rewrite the setting??"
date: 2009-05-19
forum: Server Platforms
---

### Post by bigheart on 2009-05-19
Hi i was using transmission daemon in 8.04. but after i upgraded to 9.02 i found the system created a new user called debian-transmission and it replace my transmission daemon startup script in init.d.

anyway, the transmission daemon is still functioning after the upgrade BUT i found when i changed the setting in /etc/transmission-daemon/settings.json and restart the daemon by the script in init.d, all changes will be fallback to previous.
i don't know what's going on and wish someone can help me out ...

thanks!

Joseph

---

### Post by lowph on 2009-05-31
Stop the daemon instead of restarting, edit the settings.json file and start the transmission daemon again.
Apparently the transmission daemon rewrites the file while exiting.

---

