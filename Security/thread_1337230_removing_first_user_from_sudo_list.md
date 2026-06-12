---
title: "removing first user from sudo list"
date: 2009-11-25
forum: Security
---

### Post by tapas_mishra on 2009-11-25
How can the first user be removed from sudo list I do not want to use the graphical tool

---

### Post by Lars Noodén on 2009-11-25
First, if you don't have one already, create a second user and add it to the group admin.

Look (don't change) /etc/sudoers and see the entry for the group admin.


Second, once you have the second user as a member of the group admin, and you've tested sudo to verify it, then you can remove the first user from the group admin.

```

# show current group membership
groups tapas_mishra  
 tapas_mishra adm dialout cdrom plugdev users lpadmin sambashare **admin**

# edit the user minus that group
usermod -G tapas_mishra,dialout,cdrom,plugdev,users,lpadmin,sambashare tapas_mishra

```

The details of [usermod](http://manpages.ubuntu.com/manpages/karmic/en/man8/usermod.8.html) vary from os to os.  So be sure to check the manual page first.

---

### Post by sisco311 on 2009-11-25
In Ubuntu:
```
sudo delgroup *username* *group*
```should do the trick. (remove *username* from *group*)

```
sudo gpasswd -d username group
```should work in most distros.

NOTE: The changes will take effect after you start a new login session(log out username and log it back in).

---

### Post by tapas_mishra on 2009-11-26
Thanks a lot

---

