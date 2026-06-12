---
title: "Installing programs for whole PC"
date: 2009-12-29
forum: Wine
---

### Post by J V on 2009-12-29
I want to install programs for the whole PC, this means multiple users can use it, it won't be doubling data by installing in multiple /home s, and /home backups won't take forever saving tons of windows applications.

Is there a way to make wine save ALL applications to the same spot on the harddrive?

Possibly under /usr/wine or something?

---

### Post by gsmanners on 2009-12-29
Actually, you could create a shared folder like /wine for the C: drive, then use this command (every user would have to do this):

ln -s /wine ~/.wine/dosdevices/c:

Then run winecfg and see how that works out for you.

---

### Post by beastrace91 on 2009-12-29
Check it out - using a quick forum search I found a HOWTO explaining just what you are looking to do:

[HOWTO: Install Wine applications for Multiple Users](http://ubuntuforums.org/showthread.php?t=917422&highlight=howto+wine+multiple+users)

Cheers,
~Jeff

---

### Post by beastrace91 on 2009-12-29
> **gsmanners said:**
> Actually, you could create a shared folder like /wine for the C: drive, then use this command (every user would have to do this):

ln -s /wine ~/.wine/dosdevices/c:

Just saw this - just like to say this is a bad idea because you would be confusing different Wine configurations from each user + each Wine directory has its own file permissions for each said user.

Check the howto I posted above.

~Jeff

---

### Post by J V on 2009-12-30
Thanks, I always search but I coulden't find it, SOLVED :)

---

