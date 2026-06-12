---
title: "Setting up mail server for local only (non existing domain)"
date: 2012-01-28
forum: Server Platforms
---

### Post by extruct on 2012-01-28
Hi there!
I am a web developer and I have my own home server with LAMP running Ubuntu 10.04 LTS

I need mail sending on my current web site I am developing. The mails will be sent via SMTP. I don't want to use a real SMTP server (i.e. gmail or etc) instead I want to setup a local only SMTP server on my home server. I want this server to be able to send email and I want to be able to setup thunderbird to read emails from this server.

Its important to note that ALL the activity is inside my home network, the SMTP server should not receive/send email outside the home network (192.168.0.0 network). Therefore I have no real domains or email addresses. I setup virtual hosts like mysite.loc and in the testing machine I write in hosts file
```
mysite.loc 192.168.1.123 #<= Home server IP
```
I need the ability to setup different emails to send from:
[email]no-reply@mysite.loc[/email], [email]support@mysite.loc[/email] and dummy emails to receive from:
[email]user1@mysite.loc[/email], [email]user2@mysite.loc[/email] and etc.

All the tutorial I've seen relying on real domains (which I remind I dont have), hence I'm having difficulties setting up the mail server.

Any help would be appreciated. Thanks!

---

### Post by extruct on 2012-01-29
Somebody?

---

### Post by druhboruch on 2012-01-29
It doesn't matter if your domin is registered or not.
All you need is the local DNS server with SOA record and MX record pointing to your local mail server.

It will work just fine on your local network.

---

### Post by extruct on 2012-01-30
Thanks! Will try this.

---

