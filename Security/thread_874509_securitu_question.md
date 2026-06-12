---
title: "securitu question"
date: 2008-07-30
forum: Security
---

### Post by fouadk on 2008-07-30
hi everyone....

i have modified my /etc/sudoers files to the following:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

www-data        ALL=NOPASSWD:   /bin/cp, /bin/mkdir, /bin/chmod , /bin/chown
~                                                                            
```

do i need to worry about any security holes ????

please help

thanks in advance

---

### Post by p_quarles on 2008-07-30
Aside from the issue of any security problems, it seems seriously unnecessary.

In any case, I can't recall whether that syntax would give the user privileges on all domains (kind of pointless, possibly a bad idea), or as all users (in which case you are asking to have your computer owned by a scriptkiddie). Either way, there is definitely a better way of accomplishing what you want to do.

---

### Post by fouadk on 2008-07-30
i couldn't achieve similiar effect using php functions for instance mkdir and chown and chmod even thought i set the group permission to www-data

---

### Post by p_quarles on 2008-07-30
Take a look at suphp -- it's an Apache module that allows you to control how PHP runs.

---

### Post by Dr Small on 2008-07-30
Well anyhow, the syntax is wrong, unless I am mistaken. It should be:
```
www-data ALL=(ALL) NOPASSWD: /bin/cp, /bin/mkdir, /bin/chmod, /bin/chown
```

---

