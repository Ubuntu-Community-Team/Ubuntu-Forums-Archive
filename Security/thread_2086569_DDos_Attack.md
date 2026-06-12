---
title: "DDos Attack"
date: 2012-11-21
forum: Security
---

### Post by asai on 2012-11-21
Hi,

This is not really a Ubuntu question, but I need some good advice. And this is a good place to start. :)

I have a webpage set ut at one.com
Now they have blocked my access to all of one.com because they say that there has been a DDos attack from my IP address.

Any suggestions on how to search my computers for the source of this attack? I now that this is not intentionally...

---

### Post by asai on 2012-11-21
Some more information: It seems like it is one.com that blocks and register as an attack because of to many FTP uploads. Any suggestions on how to log FTP connections from my IP?

---

### Post by rnerwein on 2012-11-21
> **asai said:**
> Some more information: It seems like it is one.com that blocks and register as an attack because of to many FTP uploads. Any suggestions on how to log FTP connections from my IP?

hello
may be "netstat -punt" embedded in a script can help you - the output is:
netstat -punt
Aktive Internetverbindungen (ohne Server)
Proto Recv-Q Send-Q Local Address    Foreign Address         State       PID/Program name
tcp        0      0 192.168.2.138:56952     91.189.89.76:443        VERBUNDEN   3734/python     
tcp        1      0 192.168.2.138:38915     91.189.89.144:80        CLOSE_WAIT  3477/ubuntu-geoip-p

---

### Post by Habitual on 2012-11-21
[email]abuse@one.com[/email]

---

### Post by wildmanne39 on 2012-11-21
*Thread moved to **Security Discussions**.*

---

### Post by CharlesA on 2012-11-21
> **Habitual said:**
> [email]abuse@one.com[/email]
This. Maybe they could give you more info instead of "too much ftp traffic"

How were you transferring files to your site?

---

