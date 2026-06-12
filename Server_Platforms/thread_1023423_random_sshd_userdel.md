---
title: "random sshd userdel"
date: 2008-12-27
forum: Server Platforms
---

### Post by superheavy on 2008-12-27
I am running a server, somehow my sshd daemon died and the user sshd was deleted.  I don't know if this is cause of some error, or malevolence.  Here is the post mortem.

```

Dec 27 23:26:35 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get purge php5-cli$
Dec 27 23:26:44 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get purge php5-dev$
Dec 27 23:28:30 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get purge php5-common$
Dec 27 23:28:45 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get purge lamp-server^$
Dec 27 23:29:04 li41-49 sshd[2267]: Received signal 15; terminating.$
Dec 27 23:29:05 li41-49 userdel[10562]: delete user `sshd' $
Dec 27 23:29:31 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get purge php5-mysql$
Dec 27 23:29:39 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get autoremove$
Dec 27 23:32:16 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get update$
Dec 27 23:32:29 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get install lamp-server^$
Dec 27 23:32:55 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/apt-get install lamp-server^ php5-cli php5-dev$
Dec 27 23:33:07 li41-49 sudo:   dallas : TTY=pts/0 ; PWD=/home/dallas ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a$

```

If you notice if happens in the middle of me reinstalling stuff.  The funny thing is, the server didn't begin to refuse ssh connections till about 2 hours later.

---

### Post by atoponce on 2008-12-28
The 'lamp-server' packages not a package that I see in the main Ubuntu repos, or in the Canonical partner repo. Is this coming from a 3rd party repository that you have in your sources.lst?

If you have physical access to the machine, you could reconfigure openssh-server with the dpkg command.

---

### Post by superheavy on 2008-12-28
it's from the tasksel package system.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

