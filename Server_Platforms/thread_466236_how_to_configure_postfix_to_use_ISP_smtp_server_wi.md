---
title: "how to configure postfix to use ISP smtp server with php"
date: 2007-06-06
forum: Server Platforms
---

### Post by tarek on 2007-06-06
Hi,
I have Ubuntu 7.04 and running apache + mysql + php. I installed postfix and would like to use my ISP's smtp server.

So i have to two questions:

How can I configure postfix to use my ISP's smtp?
and
How can I make php use postfix?

thanks,
tarek

---

### Post by Mr. C. on 2007-06-06
[LIST=1]
[*]How can I configure postfix to use my ISP's smtp?

This depends on what your ISP requires for connecting to their SMTP server.  Do they require authentication?


[*]How can I make php use postfix?

In your /etc/php.ini file, you configure:

sendmail_path = /usr/sbin/sendmail -t -i

which will use postfix's sendmail compatibility application.

[/LIST]

---

### Post by tarek on 2007-06-06
No authentication is required, just smtp.eastlink.ca

I used to send emails using php on windows by modifying the smtp variable in php.ini

not sure how to do it now in ubuntu.

thanks.

---

### Post by Mr. C. on 2007-06-06
In that case, search for and review "relayhost" in man 5 postconf.  

```
man 5 postconf | less +/^relayhost
```

Relayhost will allow you to configure mail to be fowarded to smtp.eastlink.ca for domains that do not match your own.

MrC

---

### Post by tarek on 2007-06-08
I reconfigured postfix and selected smarthost then entered my ISP smtp server but it didn't until I restarted ubuntu!

I thought it would work without having to reboot.

It's working now, thanks!

tarek

---

### Post by Mr. C. on 2007-06-08
You probably only needed to restart the postfix service:

/etc/init.d/postfix restart

MrC

---

### Post by tarek on 2007-06-08
> **Mr. C. said:**
> You probably only needed to restart the postfix service:

/etc/init.d/postfix restart

MrC

Tried that but nothing happened. Atfer editing files and restarting services I gave up yesterday and forgot about it until 10 minutes ago I restarted my pc and suddenly received the emails I was trying to send to my gmail yesterday.

---

