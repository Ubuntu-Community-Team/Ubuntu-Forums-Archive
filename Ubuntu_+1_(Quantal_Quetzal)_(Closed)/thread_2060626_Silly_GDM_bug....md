---
title: "Silly GDM bug..."
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sgage on 2012-09-20
It seems that if you set GDM for autologin at boot, you can't log out of a session - it just immediately logs right back in. Not sure when this behavior began, since I only just enabled autologin today, but I suspect it was yesterday's upgrade from 3.5.91 to 3.5.92.

---

### Post by dino99 on 2012-09-20
not seen this issue on i386 here, but i've let lightdm managed the login (both gdm & lightdm installed).
maybe you can purge then reinstall them.

---

### Post by sgage on 2012-09-20
> **dino99 said:**
> not seen this issue on i386 here, but i've let lightdm managed the login (both gdm & lightdm installed).
maybe you can purge then reinstall them.

I'm running the Gnome Remix, so no lightdm was ever installed on this system and is not really an issue. I suppose I could try reinstalling gdm... [edit: reinstalling didn't help. I've replicated this several times now - enable autologin, the problem appears, disable autologin, I am able to logout as normally.]

---

