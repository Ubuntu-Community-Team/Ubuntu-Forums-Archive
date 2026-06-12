---
title: "SFTP rejecting logon"
date: 2005-01-02
forum: Server Platforms
---

### Post by jjeffers on 2005-01-02
Hopefully this is not a dumb question.  I've looked around this forum, the Ubuntu Wiki, Google, etc. and can't find an answer.

I've installed SSH, and I can connect to my server with no problem, but I can't SFTP to it.  This is all on the same subnet, so there are no firewalls in between the client and server.  I've tried using SFTP with WS_FTP Pro 9 and the SFTP client built in to Dreamweaver MX 2004.  No luck with either--both say my user credentials are being rejected.  WS_FTP gives me a little more info in the logs:

```

Finding Host myhost.mydomain.com ...Connecting to 10.0.0.10:22
Connected to 10.0.0.10:22 in 0.000000 seconds, Waiting for Server Response
Server Welcome: SSH-2.0-OpenSSH_3.8.1p1 Debian 1:3.8.1p1-11ubuntu3.1
Client Version: SSH-2.0-WS_FTP-9.0-2004.06.17
DSS Signature Verified
Session Keys Created
Ciphers Created
New Client->Server ciphers in place.
New Client->Server ciphers in place.
Completed SSH Key Exchange.  New Keys in place
Failed SSH User Authentication
SSH Transport closed

```I can connect to other SFTP servers with these apps.  Any ideas?

EDIT: One other thing...where are SFTP connection attempts logged?  I thought they'd be in /var/log/auth.log, but I don't see them there.

---

### Post by jjeffers on 2005-01-02
Found the problem.  I had to comment out

PasswordAuthentication no

in /etc/ssh/sshd_config

---

### Post by hypatia on 2006-02-20
Yeah so sorry to resurrect a dead thread... but for noobs such as myself, don't forget to restart sshd:

```
sudo /etc/init.d/ssh restart
```

---

### Post by Data-Base on 2007-05-26
hello,

sorry to bring that back again

i use DW CS3 and I'm not able to connect !!!!

how I can see the logs and (it worked fine for me when I used to use SuSE) !!!

Thank you

---

