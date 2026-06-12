---
title: "Running program as different user (without password)"
date: 2008-09-18
forum: Security
---

### Post by vkov_tinsky on 2008-09-18
Hi,

I'm trying to run a program as a different user (but not root) without being prompted for a password. I read up on sudoers and thought the following addition to /etc/sudoers would do the trick (where my user is **vt** and I want to run */usr/bin/top* as user **rawvb**):
```
vt ALL=(rawvb) NOPASSWD: /usr/bin/top
```
However when I run the following I still get prompted for a password:
```
sudo -u rawvb /usr/bin/top
```

I've searched these forums but couldn't find any threads detailing this (they all seem to be about running certain commands as root).


Regards,
VT

***** Edit *****
I found [_this_](http://ubuntuforums.org/showthread.php?t=690102) thread which doesn't have a solution however.

---

### Post by cdenley on 2008-09-18
> **vkov_tinsky said:**
> Hi,

I'm trying to run a program as a different user (but not root) without being prompted for a password. I read up on sudoers and thought the following addition to /etc/sudoers would do the trick (where my user is **vt** and I want to run */usr/bin/top* as user **rawvb**):
```
vt ALL=(rawvb) NOPASSWD: /usr/bin/top
```
However when I run the following I still get prompted for a password:
```
sudo -u rawvb /usr/bin/top
```

I've searched these forums but couldn't find any threads detailing this (they all seem to be about running certain commands as root).


Regards,
VT

***** Edit *****
I found [_this_](http://ubuntuforums.org/showthread.php?t=690102) thread which doesn't have a solution however.

That's odd, becuase this line works correctly for me
```

cdenley ALL=(rawvb) NOPASSWD: /usr/bin/whoami

```
```

cdenley@ubuntu:~$ sudo -K
cdenley@ubuntu:~$ sudo -u rawvb whoami
rawvb

```

---

### Post by vkov_tinsky on 2008-09-18
What can I say... I'm running Xubuntu 8.04 and all I have in /etc/sudoers is:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
vt	ALL=(rawvb) NOPASSWD: /usr/bin/top

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

And obviously when I run *sudo -u rawvb top* I get the password prompt cancelling which adds to /var/log/auth.log:
```
ogimogi sudo:       vt : pam_authenticate: Conversation error ; TTY=pts/0 ; PWD=/home/vt ; USER=rawvb ; COMMAND=/usr/bin/top
```

The only possibly related thing I can think off is that I installed the *libpam-gnome-keyring* package (so automatically retrieve the key for my wireless connection upon login). Or do I maybe have to set something in System->Authorizations?

Any suggestions would be appreciated.

Regards,
VT

---

### Post by cdenley on 2008-09-18
I think you might have to add the NOPASSWD line at the end.

---

### Post by vkov_tinsky on 2008-09-19
> **cdenley said:**
> I think you might have to add the NOPASSWD line at the end.

D'oh! That's exactly what it was, thanks :)

Regards,
VT

---

