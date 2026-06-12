---
title: "Postfix configuration"
date: 2010-11-05
forum: Server Platforms
---

### Post by ryushi5 on 2010-11-05
Let me start off by saying I am experienced with computers, though my knowledge of Linux and networking is limited. I've just recently started setting up a Ubuntu 10.04 server to be a SMTP server. 

I've followed this guide by the letter:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

What I've attempted, to test the server, is the following:

telnet localhost 25
ehlo localhost

(this returns all the desired information)

I then do a MAIL FROM my domain which is accepted, and try to do a RCPT TO an external mail server (gmail) to test sending an email. I am then told 'Relay Access Denied'. 

I'm sure that there's something fundamental that I'm either not understanding or not doing correctly. I simply want an SMTP server that can send to other domains. What do I need to do?

---

### Post by ryushi5 on 2010-11-05
Anyone have any advice?

---

