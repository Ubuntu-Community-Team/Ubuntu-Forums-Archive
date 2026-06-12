---
title: "Sudo no longer prompting for password"
date: 2011-08-16
forum: Server Platforms
---

### Post by Barry Cent on 2011-08-16
Hello,

I am suddenly not prompted for my password when I run any command as sudo on a few of my Ubuntu servers.

if I run sudo -K, the session is cleared, and I am prompted again for my password, however it saves/caches it until I run sudo -k again :-( even if I log out and back in. I want it to prompt me for my password, as it should (and did) by default, for security.

Any ideas what could be causing this?

Here's my /etc/sudoers file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Thanks,

Joe

---

### Post by saeeddeep on 2011-08-17
With timestamp_timeout=0 you will be always prompted for a password.

---

### Post by Barry Cent on 2011-08-17
My recent upgrade to Webmin 1.560 seems to have caused this issue.

I have downgraded to 1.550 and the issue seems to have gone away. Guess I'll just have to wait until the next version of Webmin is out, as this wasn't the only problem I had with 1.560 :-(.

Joe

---

