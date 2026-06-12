---
title: "Gnome on server and run levels"
date: 2008-09-03
forum: Server Platforms
---

### Post by degers on 2008-09-03
Dear All, Sorry if this has been posted hundreds of times.

What I would like is to run a Ubuntu server on a box and install a lightweight gnome by installing gnome-core from the standard server install.  This is because I am not 100% confident in my linux abilities and I wish to have a backup incase I get stupid.  Then what I wish to do is have runlevels so that I can switch on and off the Gnome system so it does not use up resources on the server when I don't need it running.  Is this possible?

Many Thanks.

---

### Post by cdenley on 2008-09-03
> **degers said:**
> Dear All, Sorry if this has been posted hundreds of times.

What I would like is to run a Ubuntu server on a box and install a lightweight gnome by installing gnome-core from the standard server install.  This is because I am not 100% confident in my linux abilities and I wish to have a backup incase I get stupid.  Then what I wish to do is have runlevels so that I can switch on and off the Gnome system so it does not use up resources on the server when I don't need it running.  Is this possible?

Many Thanks.

I think it's possible, but probably a simpler solution would be...

prevent gdm from starting automatically
```

sudo update-rc.d -f gdm remove

```

then use /etc/init.d/gdm to start/stop the graphical login.
```

sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop

```

---

