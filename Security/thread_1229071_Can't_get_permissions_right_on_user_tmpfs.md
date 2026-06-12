---
title: "Can't get permissions right on user tmpfs"
date: 2009-08-01
forum: Security
---

### Post by shaggy999 on 2009-08-01
I decided to try creating a user that gets wiped on shutdown by mounting the user directory to tmpfs. The way I did it is installed ubuntu and then deleted everything in the /home/<user> folder and then added this line to /etc/fstab:

```
none /home/<user> tmpfs size=128m,rw,mode=755 0 0
```

When I start the OS up and login I get this error:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Then I just get a black screen and a cursor that moves around.

So I rebooted into safe mode and noticed that when I mount the tmpfs it sets the owner and group of /home/<user> to root. I changed this back to the user and then typed exit and told Ubuntu to continue booting. I was able to log in as that user perfectly.

Of course, upon reboot it gets all messed up again. How do I set it up so that when it mounts it retains the owner and group that were originally set on the folder it got mounted to?

---

### Post by shaggy999 on 2009-08-01
I got it to work. Mount specifies a uid= and gid= option for the vfat filesystem. It specifies that option only for vfat, but I decided to try and see if it would work and it did. Yay.

---

