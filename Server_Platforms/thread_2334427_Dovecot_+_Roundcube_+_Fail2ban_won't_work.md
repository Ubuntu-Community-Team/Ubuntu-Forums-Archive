---
title: "Dovecot + Roundcube + Fail2ban won't work"
date: 2016-08-19
forum: Server Platforms
---

### Post by nudeltabak on 2016-08-19
Hello guys,

I am trying to ban brute force login attempts at my roundcube webpage. I can allready successfully ban imap brute force attempts at dovecot. But for roundcube it won't work.
Let's say an user 'testuser' wants to login at my roundcube front end using brute force. His public IP is 80.111.100.1 and my server public IP is 70.111.100.1 (Sorry if this aren't good example IPs)
Roundcube logs fail attempts like this:

```
[19-Aug-2016 15:01:05 +0200]: <ea7sisp2> IMAP Error: Login failed for testuser from 127.0.0.1. AUTHENTICATE PLAIN: Authentication failed. in /var/www/html/rc/program/lib/Roundcube/rcube_imap.php on line 193 (POST /rc/?_task=login&_action=login)
```

I do not get the right remote adress from testuser.
Dovecot loggs it this way:
```
2016-08-19 15:01:05 imap-login: Info: Disconnected (auth failed, 1 attempts in 2 secs): user=<testuser>, method=PLAIN, rip=70.111.100.1, lip=192.168.1.143, TLS, session=<7+xfSmt62gBQgCQz>
```

Normally, i ban all auth failed attemps in this log file with fail2ban. But because roundcube somehow writes my own IP in rip, i will block myself and not testuser's puplic IP.

Is there someone who can help?

---

### Post by Graham_Willis on 2016-08-21
Just use fail2ban's whitelisting function:

[http://www.fail2ban.org/wiki/index.php/Whitelist](http://www.fail2ban.org/wiki/index.php/Whitelist)

---

