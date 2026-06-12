---
title: "proftpd + ftpasswd problems."
date: 2006-10-11
forum: Server Platforms
---

### Post by Bograth on 2006-10-11
Just started using ubuntu on my server and so-far everything has been a learning experience. But now when it comes to the ftpserver there are some minor problems:

Installed the ftpasswd script for proftpd so that it would be easier to manege users.

Anyway, in the how-to file for ftpasswd it says:
> 
For example, to create the alternate password file in /usr/local/etc/ftpd/passwd:

ftpasswd --passwd --file=/usr/local/etc/ftpd/passwd: --name=bob --uid=1001 --home=/home/bob --shell=/bin/false

So i created a new directory:
/opt/lampp/usr

And changed the command to:
ftpasswd --passwd --file=/opt/lampp/usr/passwd: --name=ftptest --uid=1002 --home=/home/ftp --shell=/bin/false

And i get a line in the ftpasswd file as follows:
ftptest:$1$3ETIBwdw$vQJFTj/xA/oj76yDQAl5x/:1002:1002::/home/ftp:/bin/false

> 
But when I then try to connect to the server it says:
WinSock 2.0 -- OpenSSL 0.9.7d 17 Mar 2004
[R] Connecting to 192.168.1.201 -> IP=192.168.1.201 PORT=21
[R] Connected to 192.168.1.201
[R] 220 ProFTPD 1.3.0 Server (ProFTPD) [192.168.1.201]
[R] USER ftptest
[R] 331 Password required for ftptest.
[R] PASS (hidden)
[R] 530 Login incorrect.
[R] Connection failed
[R] Delaying for 120 seconds before reconnect attempt #1

Did I do this completely wrong? did I put in the right uid number? (I checked the passwd file in /etc so that it wouldn't have problems with other users). Oh and don't go too high level on me when you are explaining, I've only been using linux for 10 days.

---

### Post by Bograth on 2006-10-13
Noone who's fixed their ftpserver -users this way?

---

### Post by BadDolphin on 2006-10-16
I've spent the last few hours trying to get authentication working at all, using Ubuntu 6.06 and proftpd.  I know next to nothing about authentication, but I think I've tried every possible combination of configs, but no matter what I do I get "**no such user**" in /var/log/daemonlog (the only log I can find with relevant info in it).  I think I understand that proftpd requires PAM unless you disable it in the proftpd.conf file, but I don't know if Ubuntu requires anything special to use that.

---

