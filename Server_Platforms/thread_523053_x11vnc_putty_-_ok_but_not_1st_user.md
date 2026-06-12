---
title: "x11vnc putty - ok but not 1st user"
date: 2007-08-11
forum: Server Platforms
---

### Post by TravMan63 on 2007-08-11
confusing heading - confusing problem... (sort of)

I have putty running on an XP box. , x11vnc and ssh-server on all linux installs.

I can connect to 3 linux boxes (2, 1 box is dual boot)

Xubuntu 7.04 , Ubuntu 7.04 and Elive Gem.

I haven't confirmed this on the Elive install yet... (but have no problem connecting via ssh to Elive...) 

off point - I've also connected to vpc's (microsft virtual pc) (DSLinux VPC on XP) - why? just good exercise... and fun..



-- main point --
On both 'buntu installs - 

I can start x11vnc - but only on 2nd user accounts - the 1st user account that was created - cannot be accessed (ssh is fine...)

This is the error:

```
11/08/2007 10:46:05 *** XOpenDisplay failed. No -display or DISPLAY.
11/08/2007 10:46:05 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
11/08/2007 10:46:05 *** 1 2 3 4
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

on the xubuntu box:

```
nly@nly-desktop:~$ ps wwaux | grep auth
root      4462  2.9  6.2  21832 15832 tty7     Ss+  09:26   0:50 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
nly@nly-desktop:~$
```

I tried - demoting 1st user (so they could not administer system - n/c)

I can only connect / start x11vnc on the users added later to the system.

I do log on remotely as the user with the active display.

I'm guessing it has something to do with the magic cookie file.... I've read up on it but I"m still :confused:.


Thanks... TM

---

