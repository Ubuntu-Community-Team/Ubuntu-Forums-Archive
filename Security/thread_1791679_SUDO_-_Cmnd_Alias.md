---
title: "SUDO - Cmnd_Alias"
date: 2011-06-27
forum: Security
---

### Post by ric79 on 2011-06-27
Hi all,
I'm trying to configure /etc/sudoers for this case:

 1) MYDIR contains multiple sudirectories which must be accessible ( /bin/ls -la /MYDIR/*) by the user MYUSER.
     - Questions: how to make the CMD_Alias for "ls" general for all MYDIR subdirectories?

 2) In MYUSER crontab there is a script (/home/MYUSER/MYSCRIPT.pl) which needs running "ls" and reading files in MYDIR subdirectories 
     - Questions: how to enable reading from perl ?

Thanks
Riccardo

---

### Post by Ryan Dwyer on 2011-06-27
Sudo is not the solution here. Change the permissions on the directories/files so that the user can read them.

---

