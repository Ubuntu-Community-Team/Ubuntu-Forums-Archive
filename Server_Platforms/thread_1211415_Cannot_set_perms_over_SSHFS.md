---
title: "Cannot set perms over SSHFS"
date: 2009-07-12
forum: Server Platforms
---

### Post by robdog09 on 2009-07-12
I am using SSHFS to mount a remote file system over ssh. It works great, and lets me write files, but whenever i create a file or directory, its not setting the perms correctl. As a result, i have to ssh in and chmod -R everything i need.

My SSHFS command is below:

sshfs [EMAIL="user_xyz@xyz.com:/home/content/s/t/a/xyz.com"]user_xyz@xyz.com:/home/content/s/t/a/xyz.com[/EMAIL]/html /mnt/xyz.com-PROD -o allow_other,reconnect,password_stdin,workaround=rename,umask=022 

The crucial element here (i know) is umask. 022 should equate to 755 perms on the remote host, but all i get is 644:

-rw-r--r-- 1 xyz   inetuser     0 Jul 12 12:41 test2.html


Ideas?

---

### Post by scorp123 on 2009-07-12
Read this thread:

[http://ubuntuforums.org/showthread.php?p=7563057#post7563057](http://ubuntuforums.org/showthread.php?p=7563057#post7563057)

---

