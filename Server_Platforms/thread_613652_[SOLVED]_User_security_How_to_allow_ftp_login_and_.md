---
title: "[SOLVED] User security: How to allow ftp login and deny interactive logins"
date: 2007-11-15
forum: Server Platforms
---

### Post by Yakov Hrebtov on 2007-11-15
I want to setup user as ftp-only user.
On Fedora I can assign to user /usr/sbin/nologin shell. Such user cannot work interactively, but can work as ftp user.

On ubuntu, user with dummy shells (/usr/sbin/nologin, /bin/true for example) cannot connect as ftp user (I tested this using vsftpd server).

How can I do what I need?

Thanks in advance!

P.S. Also I wonder why almost all ubuntu system users has real /bin/sh shell!

---

### Post by stevux on 2007-11-15
about the shell/login issue;
[INDENT]Try adding '/bin/false' to the '/etc/shells' file, and give the ftp users this shell.

Actually, I would not exactly know the difference between having '/bin/true' or '/bin/false' as a shell, but i prefer 'bin/false'. If this does not work for you, maybe you should stick to '/bin/true'.

You also might want to try and set "check_shell=NO" in you 'vsftpd.conf' file.[/INDENT]


about the shells for daemon users;
[INDENT]Most likely, the daemons need a shell to perform actions, and usually envvars are an important way of setting/communicationg options.[/INDENT]

hth,

---

### Post by Yakov Hrebtov on 2007-11-15
Thanks!
Adding dummy shells to /etc/shells helps!

---

