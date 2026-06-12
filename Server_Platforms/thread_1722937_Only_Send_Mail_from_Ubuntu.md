---
title: "Only Send Mail from Ubuntu"
date: 2011-04-06
forum: Server Platforms
---

### Post by divided on 2011-04-06
I want to be able to send mail from my ubuntu server but I don't want to be able to receive mail or have to set up any email accounts.  How can I achieve this?

Any help is greatly appreciated.  Thanks in advance!

---

### Post by falko on 2011-04-06
Install Postfix and set inet_interfaces to 127.0.0.1 in /etc/postfix/main.cf. That way you can send mail, but no mail can be sent to your server.

---

### Post by divided on 2011-04-06
> **falko said:**
> Install Postfix and set inet_interfaces to 127.0.0.1 in /etc/postfix/main.cf. That way you can send mail, but no mail can be sent to your server.

Works perfectly.  Thank you!!!

---

