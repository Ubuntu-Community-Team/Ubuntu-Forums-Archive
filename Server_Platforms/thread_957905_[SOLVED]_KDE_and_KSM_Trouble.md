---
title: "[SOLVED] KDE and KSM Trouble"
date: 2008-10-24
forum: Server Platforms
---

### Post by baudday on 2008-10-24
I am sitting at college and wanted to start VNC to sort out a problem. When I tried I could not. I figured if I restarted the server and log in it would restart X and there wouldn't be the issue. So I ask someone at my house to restart the server and log back in. When they try to log back in, they get the following two errors. First, KDE could not start, then KSM server could not start. Something along those lines. After you dismiss both errors, it returns to the login screen. I have no idea what could be going on. I'm able to connect via ssh from my dorm room, and the website and everything is running. So I'm really not sure what's going on. I would appreciate any help.

Thanks

---

### Post by lykwydchykyn on 2008-10-25
See if there is a file ~/.xsession-errors in the home directory of the user you tried to log in as.  If there is, delete it, try to log in, then copy the new version of the file here.

Also, check to see if any of your partitions are full.  That can sometimes prevent login.

---

### Post by baudday on 2008-10-25
Here it is...

```
Xsession: X session started for willem at Sat Oct 25 13:45:15 CDT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kdeinit: Aborting. No write access to '/home/willem/.ICEauthority'.
Warning: connect() failed: : No such file or directory
The following installation problem was detected
while trying to start KDE:

    No write access to '/home/willem/.ICEauthority'.

KDE is unable to start.
startkde: Could not start ksmserver. Check your installation.
Warning: Cannot convert string "vlines2" to type Pixmap
ERROR: Couldn't attach to DCOP server!
startkde: Shutting down...
Warning: connect() failed: : No such file or directory
Error: Can't contact kdeinit!
startkde: Running shutdown scripts...
startkde: Done.

```

---

### Post by lykwydchykyn on 2008-10-25
> 
kdeinit: Aborting. No write access to '/home/willem/.ICEauthority'.


And right there is your problem.  KDE cannot write to this file which usually means one of three things:
 - User does not own his home directory, or doesn't have write access to it.  This is fixable with:
```

sudo chown -R willem /home/willem
sudo chmod -R u+w /home/willem

```

 - disk is full, so the user can't write to any files.  In this case, clear some space on the disk and everything should be good.

 - .ICEauthority is messed up somehow.  Delete it and KDE will recreated it on login.

---

### Post by baudday on 2008-10-27
I almost forgot to come back to this thread. That worked. Thanks a lot. I now know where to look for errors involving X.

---

