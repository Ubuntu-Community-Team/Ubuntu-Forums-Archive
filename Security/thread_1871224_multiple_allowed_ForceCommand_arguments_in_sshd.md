---
title: "multiple allowed ForceCommand arguments in sshd"
date: 2011-10-28
forum: Security
---

### Post by floobit on 2011-10-28
I would like to restrict my users to two uses of ssh: running a particular script, say /usr/local/bin/myscript.sh and regular sftp.  Using ForceCommand in /etc/sshd_config seems to restrict me to only one: I can either of:

ForceCommand /usr/local/bin/myscript.sh
ForceCommand internal-sftp

either works great, but I would like to enable them both.  If both lines are included, it parses the first and ignores the second.  Is there any way allow both commands?

Also, I'm on a production server with LTS, so am limited to openssh 4.7.  If this problem is only solvable in a newer version of openssh, which version would I need?

Thanks, all.

---

### Post by Lars Noodén on 2011-10-28
Just a wild guess, would something like this work?

```

ForceCommand /bin/sh -c '/usr/local/bin/myscript.sh; /usr/libexec/openssh/sftp-server'

```

---

### Post by floobit on 2011-12-23
Unfortunately not.  The best bet seems to be using samba for the scp needs, and use the single forcecommand.  Alas.

---

