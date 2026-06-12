---
title: "VSFTPD not recognized as a service anymore"
date: 2012-01-25
forum: Server Platforms
---

### Post by peprex on 2012-01-25
Hi,

I've worked with vsftpd and filezilla for the last week (even yesterday) with no problem. 

Actually, when I try to connect by filezilla, I get ECONNREFUSED - Connection refused by server .

So I decided to enter my server via ssh and restart de vsftp service.What was my surprise when 

```
service vsftpd restart
```told me : restart: Unknow instance: 

I'm completely lost, don't know what happened. I did anything I think. It's my first connection from last night. Any ideas ? 

Thanks in advance !

---

### Post by peprex on 2012-01-25
More information about this issue:

when i do :

```
status vsftpd
```

It returns ```
vsftpd stop/waiting
```

But I'm not able to restart it by service vsftpd restart or /etc/init.d/vsftpd restart

Please, help.

---

### Post by Zookee on 2012-01-25
Sadly I'm not expert (new to Ubuntu and Linux myself) but has the daemon hung?  It might be worth checking if it's still running (or how much cpu it's using with "top") and killing it then trying to start it again.  Failing that, I have no idea.

---

