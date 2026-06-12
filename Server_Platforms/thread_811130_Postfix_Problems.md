---
title: "Postfix Problems"
date: 2008-05-28
forum: Server Platforms
---

### Post by freebullets on 2008-05-28
I need some help installing Postfix on the latest Ubuntu.  [I followed this tutorial.]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04")  First off, here are my DNS records from freedns.afraid.org just in case i got anything wrong:
```
localserver.mooo.com	A	71.14.99.36
localserver.mooo.com	MX	10:localserver
```

When I try to telnet into it, I get this:
```
jesse@ubuntu:~$ telnet localhost pop3
Trying 127.0.0.1...
Connected to localhost
Escape character is '^]'.
+OK Hello there.
user admin
+OK Password required.
pass *****
+ERR Temporary problem, please try again later
Connection closed by foreign host.
```

Help :(

---

### Post by freebullets on 2008-05-28
Someone please help

Every time I ask a technical question anywhere on the internet, it never gets answered.  I guess I'm just a problem magnet. :rolleyes:

---

### Post by bmathis on 2008-05-28
have you checked your logs in /var/logs for any errors when you try to telnet in? Also, the pop3 protocol is not handled by Postfix.

---

### Post by freebullets on 2008-05-29
Here's my logs.  I'm pretty new to linux, btw.

---

### Post by bmathis on 2008-05-29
You have a few errors that keep popping up in the logs

```
May 29 17:32:22 ubuntu postfix/proxymap[17487]: fatal: /etc/postfix/mysql-virtual_forwardings.cf, line 1: missing '=' after attribute name: "l_admin"

and

May 25 23:40:46 ubuntu postfix/proxymap[24311]: fatal: /etc/postfix/mysql-virtual_forwardings.cf, line 1: missing '=' after attribute name: "l_admin"
May 25 23:41:44 ubuntu pop3d: authentication error: Input/output error
May 25 23:41:44 ubuntu authdaemond: failed to connect to mysql server (server=localhost, userid=mail_admin): Access denied for user 'mail_admin'@'localhost' (using password: YES)
```

I would suggest taking a second look at your /etc/postfix/mysql-virtual_forwardings.cf file and fix the l_admin error. Also ensure that you have to right password for the mysql user since you were denied access with either that password or username.

---

### Post by freebullets on 2008-05-31
Here's what's happening now:

POP3
Still getting a temporary problem error.
```
 Account: 'localserver.mooo.com', Server: 'localserver.mooo.com', Protocol: POP3, Server Response: '-ERR Temporary problem, please try again later', Port: 110, Secure(SSL): No, Server Error: 0x800CCC90, Error Number: 0x800CCC92
```

SMTP
This error when I send mail to someone in the network:
```
The rejected e-mail address was 'jesse@localserver.mooo.com'. Subject 'hee', Account: 'localserver.mooo.com', Server: 'localserver.mooo.com', Protocol: SMTP, Server Response: '451 4.3.0 <jesse@localserver.mooo.com>: Temporary lookup failure', Port: 25, Secure(SSL): No, Server Error: 451, Error Number: 0x800CCC79
```

And a relay access denied error when i send a message to someone outside the network.

---

### Post by freebullets on 2008-05-31
[SIZE=3]If you need to look at my mysql database pm me.  If you want any logs, just ask.[/SIZE]

---

### Post by freebullets on 2008-06-02
hello

---

### Post by freebullets on 2008-06-04
I have another thread at: [http://www.howtoforge.com/forums/showthread.php?t=23718](http://www.howtoforge.com/forums/showthread.php?t=23718)

---

### Post by freebullets on 2008-06-05
no one can help me with this?

---

