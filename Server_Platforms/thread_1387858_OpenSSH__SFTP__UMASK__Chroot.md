---
title: "OpenSSH / SFTP / UMASK / Chroot"
date: 2010-01-22
forum: Server Platforms
---

### Post by mokachoka on 2010-01-22
Hi all, im having a real bad time trying to configure a SFTP server that jails the users to there home directory and set everyones default file permission upload to 750.

[LIST]
[*]I have the latest Ubuntu Server installed
[*]I have the latest OpenSSH installed
[*]I have followed instructions to chroot sftp using this simple guide - [http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)
[*]Users can connect without any problems whatsoever but there default permissions when uploading files is rw-r--r-- which is not what i want.
[*]There doesnt seem to be any entry for umask in the sshd_config?
[*]I have tried adding umask *** to /etc/init.d/ssh which seems to change the values of rw-r--r-- but it seems that whatever i do it will only remove certain permissions if that makes sense? i never got more than 4 letters in the permissions?
[/LIST]Everything i have googled so far has suggested this is a known bug and cannot be resolved? Surely not?
 
Does anyone have a solution? Or can anyone point me in the right direction?

---

### Post by cdenley on 2010-01-22
[http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions](http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions)

Nevermind. After reading the comments, this probably won't work with a jail. Not a bug, just a missing feature in openssh.

---

### Post by cdenley on 2010-01-22
[http://lists.mindrot.org/pipermail/openssh-unix-dev/2009-January/027118.html](http://lists.mindrot.org/pipermail/openssh-unix-dev/2009-January/027118.html)

It looks like you have 2 options.
[LIST=1]
[*]patch/recompile openssh-server to implement the desired feature
[*]implement an alternate sftp subsytem in each chroot which sets the desired umask
[/LIST]

---

