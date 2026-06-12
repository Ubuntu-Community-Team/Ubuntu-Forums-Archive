---
title: "[SOLVED] restarting sevices as non root"
date: 2008-07-31
forum: Server Platforms
---

### Post by brocky102 on 2008-07-31
I'm trying to restart the dansguardian service from the web browser, so i need to give www-data access to restart it. If i use ```
www-data ALL=NOPASSWD: /etc/init.d/dansguardian
``` it doesn't work and even if i use ```
www-data ALL=(ALL) ALL
``` or similar it doesn't work. Any ideas?

---

### Post by windependence on 2008-07-31
Are you trying to do this in the sudoers conf file?

-Tim

---

### Post by brocky102 on 2008-07-31
yeah in /etc/sudoers. i think i got it sorted though now as i wasn't specifing /usr/sbin/dansguardian

---

### Post by Dr Small on 2008-07-31
What about trying?
```
www-data ALL=(ALL) NOPASSWD: /etc/init.d/dansguardian
```

---

### Post by brocky102 on 2008-07-31
ok i got it sorted. for those wondering my sudoers file ended up looking like ```
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
Cmnd_Alias      DANSGUARDIAN = /etc/init.d/dansguardian, /usr/sbin/dansguardian

# User privilege specification
root    ALL=(ALL) ALL
www-data ALL=NOPASSWD: DANSGUARDIAN
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%www-data ALL=NOPASSWD: DANSGUARDIAN

```

---

