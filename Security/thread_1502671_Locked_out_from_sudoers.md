---
title: "Locked out from sudoers"
date: 2010-06-05
forum: Security
---

### Post by joelgsf on 2010-06-05
A few minutes ago I accepted a suggestion from update-manager for restarting my system, such that some security updates could be effective. After restarting and login in as usual, I discovered that I could not use my adminstrative rights as a sudoer. To recover them I booted again, as root, and added my username in the "admin" group. Rebooting, all seemed well again. As an extra check I installed and ran 'chkrootkit' and nothing suspect was found.
What could have hapenned? Just a glitch in the system? Can a user disappear from a group for nothing?
What further checks can I make to be sure that my system is safe?
I'm using Ubuntu Jaunty Jakalope amd64, with kernell 2.6.28-15-generic.
TIA.
:confused:

---

### Post by bodhi.zazen on 2010-06-05
I have not seen update manager do that before. Did you change something else or add your user to a new group?

What is the output of :

```
id
```

---

### Post by joelgsf on 2010-06-05
The output is
```
uid=1000(joelgs) gid=1000(joelgs) grupos=121(admin),1000(joelgs)
```

I was just finishing some work inside a W2K VBox machine (yes, I still need "that thing" for some tasks :) ). I then closed the VM and restarted my system. It's really weird.

---

### Post by CharlesA on 2010-06-05
Can you post the output of this:```
cat /etc/sudoers
```

Do it from a root shell.

---

### Post by joelgsf on 2010-06-05
Hi CharlesA, it's just a standard sudoers definition file:

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

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by CharlesA on 2010-06-05
It looks ok.

Here is what mine looks like:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

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

---

