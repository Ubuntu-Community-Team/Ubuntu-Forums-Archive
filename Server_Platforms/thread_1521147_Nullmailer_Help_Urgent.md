---
title: "Nullmailer Help Urgent"
date: 2010-06-30
forum: Server Platforms
---

### Post by Robx610 on 2010-06-30
I'm running Ubuntu Server 9.10 in a production environment where I need to send emails from bash. My organization's email server is hosted by a 3rd party but I've never had trouble relaying mail through their SMTP server. 

I have installed Nullmailer and when I attempt to send email, I recieve this error in syslog:


Jun 30 11:34:44 cloner nullmailer[16376]: Starting delivery: protocol: smtp host: mx1.123together.com file: 1277912084.16387
Jun 30 11:34:44 cloner nullmailer[16388]: smtp: Failed: 504 5.7.4 Unrecognized authentication type.
Jun 30 11:34:44 cloner nullmailer[16376]: Sending failed:  Permanent error in sending the message
Jun 30 11:34:44 cloner nullmailer[16376]: Delivery complete, 1 message(s) remain.
Jun 30 11:35:44 cloner nullmailer[16376]: Rescanning queue.

---

