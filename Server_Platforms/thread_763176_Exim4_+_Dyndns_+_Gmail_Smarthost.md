---
title: "Exim4 + Dyndns + Gmail Smarthost"
date: 2008-04-22
forum: Server Platforms
---

### Post by mattc908 on 2008-04-22
Thats alot up there, but I set up exim4 with a dynamic dns and than using gmail as my smart host, Im not sure if its working how would I tell? Let me know if anything in the following steps that I've done improperly. I just wana allow the server to send mail.

```
dpkg-reconfigure exim4-config
```

Summary of the steps:
Split Config into small files:  No
General type of mail config: Mail sent by smarthost; no local mail
System mail name: mattc908.dyndns.org 
IP-addresses to listen on for incoming SMTP connections: 127.0.0.1
Other destinations for which mail is accepted: Blank
Visible domain name for local users: mattc908
IP address or host name of the outgoing smarthost: smtp.gmail.com
Keep number of DNS-queries minimal: Yes

Next to further set up the Gmail:
add the lines: 
     smtp.gmail.com : [email]myname@gmail.com[/email] : passwd 
     gmail-smtp.l.google.com : [email]myname@gmail.com[/email]: passwd 
to /etc/exim4/passwd.client 


So what would I go from here, what would I setup? How would I check if it can send mail?

---

### Post by mattc908 on 2008-04-23
Bump

---

### Post by mattc908 on 2008-04-24
Bump

---

### Post by mattc908 on 2008-04-25
CAN ANYONE HELP ME, All I need is a to configure exim4 with a dyndns and any smarthost. I don't know how to configure it to use my ISP's smart host.

---

### Post by mattc908 on 2008-04-25
CAN ANYONE HELP ME, All I need is a to configure exim4 with a dyndns and any smarthost. I don't know how to configure it to use my ISP's smart host.

---

### Post by drklepto on 2008-05-24
Try:

```
mail destination@domain.com
Subject: Your subject

Your message..

CTRL+D


```

eNjOy! ;)

---

