---
title: "postfix/dovecot do not seem to listen on the correct IP"
date: 2008-11-15
forum: Server Platforms
---

### Post by randomstuff on 2008-11-15
Hi,

I am trying to follow the steps outlined in the [Ubuntu Server Guide ]("https://help.ubuntu.com/8.04/serverguide/C/index.html"). I am currently trying to get Postfix + DoveCot to work on my dedicated server, but I am a bit uncertain about how to configure them correctly. 

The server is rented from a hosting company so I do not have direct access to it. It has a single network interface with a single DHCP IP (which never changes though) - there is also a hidden network interace which allows me to log in through a remote recovery console.

**EDIT (Postfix is working now):** after changing postfix to liste on the smpts port, sending emails work. Port 25 seems to be blocked on my network, which is why I could not connect. port 465 works fine though. If you have the same problem as me, enable this line in /etc/postfix/master.cf:
```
smtps     inet  n       -       -       -       -       smtpd #port 465
```

**EDIT: it appers that I actually can telnet on port 993:**

```

Trying 88.189.182.88...
Connected to mail.hxxxxxxx.stratoserver.net.
Escape character is '^]'.

```

but then it gets no further. What does that mean?

**EDIT: Dovecot works now!**

I just figured out that I cannot telnet port 993 because I am using SSL. Instead I should run

```
openssl s_client -connect 88.189.182.88:993
```

But this resulted only in the following, and then nothing.

```
CONNECTED(00000003)
```

Since it obviously established a connection, but got no further, I assumed it was a problem with my certificates. I created a new post asking for help on this and the proper setup was explained to me in [this post]("http://ubuntuforums.org/showthread.php?t=983907"), and now everything is working.

---

### Post by randomstuff on 2008-11-16
Please, there must be someone who can help me with this?

Update: Postfix is working now, but I still need help with dovecot. If you can help, please do :D

---

### Post by dulbirakan on 2008-11-20
I also tried the same guide. After the SASL configurations Postfix does not work... I dont know why, but I will try another guide. You can PM me if you want.

Try to look into /var/log/sys... and netstat -l | grep postfix

I have no smtp processes on 25...

---

### Post by dulbirakan on 2008-11-20
I think I found what was causing the problem after digging around...

the line smtpd_sasl_local_domain = in main.cf should be replaced with

smtpd_sasl_local_domain = "yourdomain.com"

ofcourse you should replace yourdomain.com with "your" domain... :)

---

