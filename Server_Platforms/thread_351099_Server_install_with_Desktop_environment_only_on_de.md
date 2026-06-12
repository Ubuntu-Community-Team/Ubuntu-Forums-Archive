---
title: "Server install with Desktop environment only on demand?"
date: 2007-02-01
forum: Server Platforms
---

### Post by Barleyman on 2007-02-01
Hi All,

This might be a stupid question, but here goes.....

I am in the process of setting up a new server for my home/small business using Ubuntu server edition. 

I am comfortable configuring and running the Server from the command line, but occasionally I just want to have access to a Desktop environment, like xfce, gnome etc.  It seems like a waste of resources to have Gnome running all the time on headless server that I only would want to have access to the Desktop environment 2% of the time.

Is there a way to install a desktop environment like fluxbox, xfce or even gnome that will only run on demand when I feel like having a Desktop environment on my server?

like ssh to me@myserver, startx, start vncserver, .......? then shutdown when I am done?:confused:

---

### Post by kpatz on 2007-02-01
You could delete any symlinks to /etc/init.d/gdm from /etc/rcN.d (where N is your default runlevel); this would stop gdm (Gnome) from starting up on system boot.  Then do:```
/etc/init.d/gdm start
``` to start Gnome when you want to use it, and ```
/etc/init.d/gdm stop
``` to stop it afterward.

There's probably other ways, such as running gdm from a prompt using a bash script in non-daemon mode, then having it exit afterward.

---

### Post by Barleyman on 2007-02-01
Thanks a lot for your response, I might give that a try.

---

### Post by Littleweseth on 2007-02-02
>  	You could delete any symlinks to /etc/init.d/gdm from /etc/rcN.d (where N is your default runlevel); this would stop gdm (Gnome) from starting up on system boot. Then do:

Better and friendlier solution : aptitude install rcconf, and use that to unset the flag for GDM on all runlevels. Works like a charm :)

---

