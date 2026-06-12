---
title: "Unlock disabled"
date: 2008-08-19
forum: Security
---

### Post by berryrag on 2008-08-19
I just finished installing xubuntu.. and when I try to change settings anywhere it doesn't let me. I see the Unlock button on some screens but it's always disabled.

How do I unlock this so I can make changes?

All I've done is created the standard user it asked me to when I installed the OS and I'm logged in as that user.

---

### Post by jerome1232 on 2008-08-19
can you post the output of
```
groups
```

---

### Post by berryrag on 2008-08-19
Here's the output of groups: 

> berryrag adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare


Also, with xubuntu, is there a way to be able to make it so I can copy/paste/create new folders in places where it doesn't let me?

---

### Post by Darvids0n on 2008-10-07
Try this: [http://ubuntuforums.org/showthread.php?t=813738](http://ubuntuforums.org/showthread.php?t=813738)

Essentially, in terminal type
```
ck-list-sessions
```

And if you get no output, then type
```
ck-launch-session
ck-list-sessions
```

And see if some session info appears. If that's the case, add a script that runs ck-launch-session to /etc/init.d and append it to startup processes with
```
sudo update-rc.d <scriptname> multiuser 13
```

such that it's ensured running for multiple users, and priority 13 (starts after dbus).

Script to do all that for you:
```
sudo echo "#! /bin/sh
ck-launch-session
" > /etc/init.d/ck; sudo update-rc.d ck multiuser 13
```

Someone please correct me if I'm too n00b to know how to properly use update-rc.d, but it seems to work on a basic level for me. At least, I can unlock my nm-applet now. A few of the unlocks are still grayed, but I suppose that'd be a different issue..

---

