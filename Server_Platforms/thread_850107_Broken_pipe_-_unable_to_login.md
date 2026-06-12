---
title: "Broken pipe - unable to login"
date: 2008-07-05
forum: Server Platforms
---

### Post by satimis on 2008-07-05
Hi folks,


Ubuntu LAMP 6.06 amd64
Postfix
Cyrus
SquirrelMail.


For unknown reason I can't login on SquirrelMail.  Previsous it worked.  

What I have done recently;```

- install SugarCRM on this box, having played around on /etc/hosts, hosts.allow and hosts.deny

- ISP has changed the router which is supplied by them

```


On local pc (IP : 192.168.0.10) browser run;```

https://192.168.0.52/squirrelmail/src/login.php
Login;
ERROR: Connection dropped by IMAP server.

```


$ tail /var/log/mail.err```

Jul  5 18:35:34 satimis cyrus/imap[4523]: refused connection from localhost.localdomain
Jul  5 18:37:35 satimis cyrus/imap[4523]: refused connection from localhost.localdomain
Jul  5 18:40:45 satimis cyrus/imap[4429]: refused connection from localhost.localdomain
Jul  5 18:47:51 satimis cyrus/imap[4429]: refused connection from localhost.localdomain
Jul  5 18:48:26 satimis cyrus/imap[4429]: refused connection from localhost.localdomain
Jul  5 19:09:09 satimis cyrus/imap[4408]: refused connection from localhost.localdomain
Jul  5 19:09:13 satimis cyrus/imap[4408]: refused connection from localhost.localdomain
Jul  5 19:21:12 satimis cyrus/imap[4398]: refused connection from localhost.localdomain
Jul  5 19:21:33 satimis cyrus/imap[4398]: refused connection from localhost.localdomain
Jul  5 19:28:14 satimis cyrus/imap[4429]: refused connection from localhost.localdomain

```


$ cat /etc/hosts.allow```

sshd: 127.0.0.1
pop3, imap : 127.0.0.1/255.0.0.0

# Domain
sshd: satimis.com

sshd sshd1 sshd2 : ALL : ALLOW

ALL: satimis.com 192.168.0.10 *.satimis.com

```


$ cat /etc/hosts.deny```

......
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID


sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log

ALL: ALL

```


$ imtest -m login localhost```

failure: prot layer failure

```


$ imtest -m login localhost.localdomain```

failure: prot layer failure

```


$ sudo netstat -an | grep tcp```

tcp        0      0 0.0.0.0:2401            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:865             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:45769           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:622             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2000          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.52:53         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.52:631        0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp6       0      0 :::993                  :::*                    LISTEN     
tcp6       0      0 :::995                  :::*                    LISTEN     
tcp6       0      0 :::2222                 :::*                    LISTEN     
tcp6       0      0 :::110                  :::*                    LISTEN     
tcp6       0      0 :::143                  :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::25                   :::*                    LISTEN     
tcp6       0      0 :::443                  :::*                    LISTEN     
tcp6       0   0 ::ffff:192.168.0.52:2222 ::ffff:192.168.0.10:50710 ESTABLISHED
tcp6       0   0 ::ffff:192.168.0.52:2222 ::ffff:192.168.0.10:50583 ESTABLISHED

```


$ grep admins /etc/cyrus.conf```

admins: cyrus

```


Please shed me some light how to fix the problem.  TIA


B.R.
satimis

---

### Post by MJN on 2008-07-05
[Edit - Sorry, scrap this - I didn't spot your mail.err file]

Check your mail log.

(By the way, where did you get the 'broken pipe' bit in the subject? I didn't see it in any of your content)

Mathew

---

### Post by MJN on 2008-07-05
It might be worth you trying adding localhost.localdomain to your hosts.allow file.

Mathew

---

### Post by satimis on 2008-07-05
> **MJN said:**
> It might be worth you trying adding localhost.localdomain to your hosts.allow file.
Hi Mathew,


Your advice works for me.


$ cat /etc/hosts.allow```

....
sshd sshd1 sshd2 : ALL : ALLOW

ALL: satimis.com *.satimis.com localhost.localdomain

```

You save me another half day poking around on Internet.


On installing SugarCRM I also played around on /etc/hosts, /etc/hosts.allow and /etc/hosts.deny.  Otherwise I can't login SugarCRM.  These 3 files seem quite important governing login permission.


A side question after having made change on these files sometimes I have to reboot.  Another time it doesn't need.  What is the problem.  Any solution to avoid a reboot?  TIA


B.R.
satimis

---

