---
title: "OpenSSH (sftp) ignores permissions"
date: 2012-02-28
forum: Security
---

### Post by ASPCartman on 2012-02-28
For example, two users: me and public. Both are in group "share".
su
[noparse]chown me:public ./lol[/noparse]
chmod go-rwx  ./lol
(no one, except me, has **any** access to this folder)

on remote:
sftp [email]public@myhost.com[/email]
sftp>cd /path/to/lol
sftp>ls
*lol contents*
...
......WTF?!
More than that i can updload, download and delete files there. 

SFTP completely ignores file ownership/permissions. I have full root access to everything everywhere (Users are being chrooted to common share directory and stay there). Help please.

---

### Post by CharlesA on 2012-02-28
Check the permissions. Check what the command you ran did: chmod go-rwx ./lol

---

### Post by spynappels on 2012-02-28
> **ASPCartman said:**
> 
[noparse]chown me:public ./lol[/noparse]


Is this correct? This suggests that public is a group rather than a user, the : separates user from group.

---

