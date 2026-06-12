---
title: "Really need help setting up mail server!"
date: 2008-06-10
forum: Server Platforms
---

### Post by freebullets on 2008-06-10
[SIZE="2"][FONT="Lucida Console"][COLOR="Navy"]I've been trying to set up a mail server for the past few weeks.  So far, it hasn't worked out too well.  If you need remote access to the machine, let me know and I'll be willing to let you tinker with it.  Anyways, here's what's happening:[/COLOR]

When I try to telnet into pop3 I get this: 
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

This error when I try to send an email to someone on the network:
```
The rejected e-mail address was 'jesse@localserver.mooo.com'. Subject 'hee', Account: 'localserver.mooo.com', Server: 'localserver.mooo.com', Protocol: SMTP, Server Response: '451 4.3.0 <jesse@localserver.mooo.com>: Temporary lookup failure', Port: 25, Secure(SSL): No, Server Error: 451, Error Number: 0x800CCC79
```

And this error when I try to send mail to users outside the network:
```
Relay access denied.
```

ANY help greatly appreciated. ](*,)[/FONT][/SIZE]

---

### Post by hyper_ch on 2008-06-10
I followed the perfect howto ([http://www.howtoforge.com](http://www.howtoforge.com)) for setting up my server on debian and it works.

---

### Post by gtdaqua on 2008-06-10
do you want to try any open-source readily-available email servers? Zimbra, Citadel perhaps...

---

