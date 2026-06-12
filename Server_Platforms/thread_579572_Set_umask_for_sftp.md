---
title: "Set umask for sftp"
date: 2007-10-18
forum: Server Platforms
---

### Post by warpforge on 2007-10-18
I need to set a umask for sftp to force new files and folders to be group-writable. Editing /etc/profile and restarting sshd doesn't seem to work for sftp. Default ACLs are also ignored by sftp.

---

### Post by TrioTorus on 2007-12-08
I have the exact same problem. Did you find a solution in the end?
I even tried:
point sftp subsystem to a shell script; in /etc/ssh/sshd_config:
```
Subsystem sftp /usr/local/lib/openssh/sftp-server.sh
```
sftp-server.sh:
```
#!/bin/bash

# This is a wrapper around the sftp-server subsystem to set umask. Point the subsystem in /etc/ssh/sshd_config to this file. (Ubuntu/Debian file locations assumed)
umask 002
/usr/lib/openssh/sftp-server
```

But even that doesn't seem to work.

Any other ideas?

---

### Post by Jason DeRose on 2008-01-14
I got this working okay by adding a "umask 007" line in /etc/init.d/ssh.

Change the top of your /etc/init.d/ssh script so it reads like this:

```

#! /bin/sh

### BEGIN INIT INFO
# Provides:		sshd
# Required-Start:	$network $local_fs $remote_fs
# Required-Stop:
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	OpenBSD Secure Shell server
### END INIT INFO

umask 007

```

Just change the "007" to "002" if that's what you want instead.

---

### Post by geek.au on 2008-02-06
> **TrioTorus said:**
> I have the exact same problem. Did you find a solution in the end?
I even tried:
point sftp subsystem to a shell script; in /etc/ssh/sshd_config:
```
Subsystem sftp /usr/local/lib/openssh/sftp-server.sh
```
sftp-server.sh:
```
#!/bin/bash

# This is a wrapper around the sftp-server subsystem to set umask. Point the subsystem in /etc/ssh/sshd_config to this file. (Ubuntu/Debian file locations assumed)
umask 002
/usr/lib/openssh/sftp-server
```

But even that doesn't seem to work.

Any other ideas?

Did you make your wrapper script executable?

# chmod ugo+x /usr/local/lib/openssh/sftp-server.sh

---

### Post by mikec13 on 2008-06-13
Did you ever get this working?

---

### Post by freexe on 2008-06-26
It's worth checking that it's not already working. It seems to preserve permissions on the copy, so if the file you are copying has 664 on it, it will keep it on the other side. Same with 644, which is why all my test were failing.

---

