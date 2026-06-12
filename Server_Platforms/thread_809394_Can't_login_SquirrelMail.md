---
title: "Can't login SquirrelMail"
date: 2008-05-27
forum: Server Platforms
---

### Post by satimis on 2008-05-27
Hi folks,


Network
Server-1 a working LAMP server
local IP - 192.168.0.10

Server-2 a newly built LAMP server
loval IP - 192.168.0.52 (without port forwarded )


Server 2
Ubuntu 6.05 drake amd65
postfix 2.2.10
SquirrelMail 2:1.4.6
uw-imapd  7:2002edebian
uw-imapd-ssl  7:2002edebian


the building of Server-2 has been completed.  

It can send emails.  
It can also receive emails if with port 25 forwarded to its local IP


On Server-1 browser running "https://192.168.0.52/squirrelmail/src/login.php"

SquirrelMail starts but unable to login with warning "ERROR: Connection dropped by IMAP server" prompted finally.


$ tail /var/log/auth.log```

May 27 22:19:01 lampserver sudo:  satimis : TTY=pts/1 ; PWD=/home/satimis ; USER=root ; COMMAND=/usr/bin/nano /var/spool/postfix/var/run/saslauthd/mux.accept
May 27 22:19:14 lampserver sudo:  satimis : TTY=pts/1 ; PWD=/home/satimis ; USER=root ; COMMAND=/usr/bin/nano /var/spool/postfix/var/run/saslauthd/saslauthd.pid
May 27 22:39:01 lampserver CRON[4525]: (pam_unix) session opened for user root by (uid=0)
May 27 22:39:01 lampserver CRON[4525]: (pam_unix) session closed for user root
May 27 23:07:36 lampserver sshd[4552]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.10  user=satimis
May 27 23:07:37 lampserver sshd[4552]: Failed password for satimis from 192.168.0.10 port 60350 ssh2
May 27 23:07:45 lampserver sshd[4552]: Accepted password for satimis from 192.168.0.10 port 60350 ssh2
May 27 23:07:45 lampserver sshd[4554]: (pam_unix) session opened for user satimis by (uid=0)
May 27 23:09:01 lampserver CRON[4574]: (pam_unix) session opened for user root by (uid=0)
May 27 23:09:01 lampserver CRON[4574]: (pam_unix) session closed for user root

```


$ tail /var/log/mail.log```
 
May 27 22:22:11 lampserver cyrus/ctl_cyrusdb[4523]: done checkpointing cyrus databases
May 27 22:22:11 lampserver cyrus/master[3881]: process 4523 exited, status 0
May 27 22:52:11 lampserver cyrus/master[4540]: about to exec /usr/sbin/ctl_cyrusdb
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: checkpointing cyrus databases
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: archiving database file: /var/lib/cyrus/annotations.db
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: archiving log file: /var/lib/cyrus/db/log.0000000001
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: archiving database file: /var/lib/cyrus/mailboxes.db
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: archiving log file: /var/lib/cyrus/db/log.0000000001
May 27 22:52:11 lampserver cyrus/ctl_cyrusdb[4540]: done checkpointing cyrus databases
May 27 22:52:11 lampserver cyrus/master[3881]: process 4540 exited, status 0

```


Please help.  TIA


Edit:


$ mutt -f imap://localhost/```

....
....
authentication (PLAIN)....
sasl authentication fail

```


B.R.
satimis

---

### Post by Titan8990 on 2008-05-27
What do you get when you go to [https://192.168.0.52/squirrelmail/src/configtest.php](https://192.168.0.52/squirrelmail/src/configtest.php)?

What IMAP and SMTP daemons are you using?

---

### Post by satimis on 2008-05-27
> **Titan8990 said:**
> What do you get when you go to [https://192.168.0.52/squirrelmail/src/configtest.php](https://192.168.0.52/squirrelmail/src/configtest.php)?

Hi Titan8990,

[https://192.168.0.52/squirrelmail/src/configtest.php?](https://192.168.0.52/squirrelmail/src/configtest.php?)```

Forbidden

You don't have permission to access

```


> 
What IMAP and SMTP daemons are you using?
$ ps -aux | grep imap```

Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
satimis   4445  0.0  0.0   3940   896 pts/0    R+   07:02   0:00 grep imap

```

$ ps -aux | grep smtp```

Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
satimis   4447  0.0  0.0   3944   904 pts/0    S+   07:03   0:00 grep smtp

```

B.R.
satimis

---

### Post by juan@forum on 2008-05-27
you have problems with your imap software...


try to connect in the command line

$ telnet 192.168.0.52 143

---

### Post by satimis on 2008-05-27
> **juan@forum said:**
> you have problems with your imap software...


try to connect in the command line

$ telnet 192.168.0.52 143
Hi juan@forum,


On Server-1 Xterm run;

$ telnet 192.168.0.52 143```

Trying 192.168.0.52...
Connected to 192.168.0.52.
Escape character is '^]'.
ehlo satimis.com

```
It hangs there.  I have to close the Xterm window.


B.R.
satimis

---

### Post by jaripetteri on 2008-07-12
I have also problems to connect to configtest.php, did you manage to get it runnung?

---

### Post by satimis on 2008-07-12
> **jaripetteri said:**
> I have also problems to connect to configtest.php, did you manage to get it runnung?
Hi jaripetteri,


I solved the problem already which came from cyrus-imap, nothing in connection with SM.


B.R.
satimis

---

### Post by jaripetteri on 2008-07-12
Just figure it out, I had configtest.php set not accessable on apache2 config... RTFM ;)

---

### Post by satimis on 2008-07-12
> **jaripetteri said:**
> Just figure it out, I had configtest.php set not accessable on apache2 config... RTFM ;)
Nice to hear you solved your problem.


satimis

---

### Post by Sargalus on 2010-02-28
I am getting the famous

You don't have permission to access /squirrelmail/src/configtest.php on this server.

I am at a lost here I can telnet to localhost 143 and connect fine both my imapd and sendmail demons are running

Im also getting the following error when I go to [http://192.168.1.103/squirrelmail](http://192.168.1.103/squirrelmail) and try to login

Error connecting to IMAP server: tls://localhost.
0 : 

which I researched back to the permission error, and now im at a lost. any help would be greatly appreciated.

---

