---
title: "Why root permissions required for creation of RAW Socket"
date: 2009-04-27
forum: Security
---

### Post by anilgurwara on 2009-04-27
To create RAW socket in Unix/Linux why should one have root permissions?
Any other work around to create raw sockets in Unix/Linux using a normal login id? Since I don't have super user credentials and I want to create RAW sockets.
Let me know if you are aware of any work around.

---

### Post by DGortze380 on 2009-04-27
> **anilgurwara said:**
> To create RAW socket in Unix/Linux why should one have root permissions?
Any other work around to create raw sockets in Unix/Linux using a normal login id? Since I don't have super user credentials and I want to create RAW sockets.
Let me know if you are aware of any work around.

Try localhost??

I think access to the TCP/IP Stack requires root privileges though.

---

### Post by anilgurwara on 2009-04-27
No, you need not have root login to access TCP/IP stack.
There must be some way out to create raw sockets without having root login.

---

### Post by bodhi.zazen on 2009-04-27
> **anilgurwara said:**
> To create RAW socket in Unix/Linux why should one have root permissions?[/code]

Yes :)

[quote]Any other work around to create raw sockets in Unix/Linux using a normal login id? Since I don't have super user credentials and I want to create RAW sockets.
Let me know if you are aware of any work around.

The "work around" is to discuss your needs with your system administrator so you may have the privileges you need ;) .

---

