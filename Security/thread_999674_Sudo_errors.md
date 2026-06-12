---
title: "Sudo errors"
date: 2008-12-02
forum: Security
---

### Post by LebLinux on 2008-12-02
Hello, I tried to add a new user to the sudoers file and after I saved the file i got errors:

sudo: parse error in /etc/sudoers near line 20

I can't run sudo anymore any ideas how to solve this?

---

### Post by sisco311 on 2008-12-02
Reboot in recovery mode and edit the sudoers file:
```
EDITOR=nano && visudo
```

the default file looks like this:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#

# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset,insults

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


set the correct permissions:
```
chown root:root /etc/sudoers
```
```
chmod 0440 /etc/sudoers
```
boot in normal mode:
```
exit
```

if you want to edit the file in a safe fashion then use visudo:
```
sudo visudo
```

users in ther admin group can use sudo.
to add a user to the group:
```
sudo adduser *loginname* admin
```

---

