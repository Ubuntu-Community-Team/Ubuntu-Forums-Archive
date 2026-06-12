---
title: "Pure-ftpd upload problem!"
date: 2011-06-23
forum: Server Platforms
---

### Post by mohs3n on 2011-06-23
Hi everybody.

I've just installed pure-ftpd on my brand new xen VPS with ubuntu 10.04 LTS , ftp service is up/run and everything is working find except that i cannot upload a file with more than 188KB in size!
I havent set any upload/download restrictions but i get this error :

```
Error:    Connection timed out
Error:    File transfer failed after transferring 188 KB in 21 seconds
```I've increased everything for my test user :

```
root@srv3152:/# pure-pw show test

Login              : test
Password           : $1$pDEwW1/0$BJX9fsGKK8EQUy7tfKRLh1
UID                : 2001 (ftpuser)
GID                : 2001 (ftpgroup)
Directory          : /home/FTP/mooli/./
Full name          : 
Download bandwidth : 3531008 Kb (enabled)
Upload   bandwidth : 3531008 Kb (enabled)
Max files          : 100000000 (enabled)
Max size           : 100000000 Mb (enabled)
Ratio              : 100000000:0 (enabled:unlimited)
Allowed local  IPs : 
Denied  local  IPs : 
Allowed client IPs : 
Denied  client IPs : 
Time restrictions  : 0000-0000 (unlimited)
Max sim sessions   : 0 (unlimited)


```

Still doesnt work... :confused:

Little help please :lolflag:

---

### Post by falko on 2011-06-23
Do you use somw sort of quota(e.g. quota inside of PureFTPd, or file system quota if you use system users as FTP users)?

---

### Post by mohs3n on 2011-06-23
No , no quota anywhere .

---

### Post by mohs3n on 2011-06-24
10 hours and no answers? , really? , so there is no one who could solve this problem?!!!

---

### Post by Lars Noodén on 2011-06-24
> **mohs3n said:**
> 10 hours and no answers? , really? , so there is no one who could solve this problem?!!!

You're barking up the wrong tree.  [FTP is not secure](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#Background_of_FTP) and for most uses, FTP is deprecated.  Try SFTP.  It is built into the openssh package.

---

### Post by mohs3n on 2011-06-24
> **Lars Noodén said:**
> You're barking up the wrong tree.  [FTP is not secure]("http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#Background_of_FTP") and for most uses, FTP is deprecated.  Try SFTP.  It is built into the openssh package.


Good answer , but anyway the problem was not the Pure-ftpd server , it was a filezilla's ftp client bug, i was using filezilla 3.3.3 and this version cannot encrypt data transfer .
I've installed the latest version 3.5 and everything works fine now .

---

### Post by Lars Noodén on 2011-06-24
Good to hear it works again.

FileZilla also supports SFTP.  So you might try working with that protocol a bit and then, when you are ready, turn off and remove FTP.

---

### Post by mohs3n on 2011-06-24
I've actually did that , i removed FTP and configured chrooted SFTP and it works like a charm .
Thanks man...

---

