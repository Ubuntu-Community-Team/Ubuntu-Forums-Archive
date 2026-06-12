---
title: "proFTP &amp; Web Script permissions issue"
date: 2018-01-15
forum: Server Platforms
---

### Post by restos on 2018-01-15
Hi,

I'm new to linux and ubuntu server. I've trying to resolve one issue searching in this and another online forms but I can't...

I'm running proFTP server in a local machine. I've created one user, user1. This user can upload and download in /home/user1directory/. Using filezilla and these credentials, I can upload and download files succesfully.

I also have a php script in a remote server. Using the same credentials in the script, I can connect to my local FTP server, list files and download using the php script, but script can't upload or delete files. I really need to upload using this script.

The permissions for directory are:
```
drwxrwxrwx  4 user1 user1  4096 ene 15 19:54 user1directory
```

I think there is an issue with permissions or user group but I can't see how to fix.

Thank you for your time.

Jose

---

### Post by TheFu on 2018-01-15
Can you use a more secure transfer like sftp?

We stopped using plain FTP about 15 yrs ago.

---

### Post by restos on 2018-01-15
Yes I will use SFTP, now I&#8217;m in testing stage.

thanks

---

### Post by TheFu on 2018-01-15
> **restos said:**
> Yes I will use SFTP, now I’m in testing stage.

thanks

Depending on requirements, sftp/scp is a much better choice, usually.  If you use ssh-keys (avoid passwords over the internet), and fail2ban and normal firewall restrictions to block "the world", it is a fairly nice system that can be easily automated.  rsync uses ssh+keys by default, if they are available.  That's good with mirroring a directory structure; adding new files or keeping a true mirror by deleting files too.

Plus every networked OS has great ssh/scp/sftp clients.  Most have rsync too.

IMHO, the greatest human discoveries/inventions, in order, are:
* wheel
* fire
* Unix
* ssh
* rsync
* germ theory

;)  People coming from other OSes haven't usually been exposed to ssh and/or rsync. These tools can do amazing things. ssh is the swiss-army-knife for secure, convenient, system-to-system connectivity.

---

### Post by LHammonds on 2018-01-15
I have not used ProFTP.  But if you want to try out vsftpd, I have a [tutorial ]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228")you can go through to set one up.

LHammonds

---

