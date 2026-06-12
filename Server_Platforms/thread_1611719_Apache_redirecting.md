---
title: "Apache redirecting?"
date: 2010-11-02
forum: Server Platforms
---

### Post by Glencore on 2010-11-02
Hello I have a MS Exchange server at work that hosts a web site as well as web access to exchange.

website is xyz.com
exchange web access is xyz.com/exchange

A new server will be set up with its a public IP address running Ubuntu Server LAMP. the domain xvz.com will have its www record linked to that new servers IP. Can people that enter xyz.com/exchange still be sent to the old exchange server though? Whats the best way to go about this?

Kind Regards,
Glen

---

### Post by Ryan Dwyer on 2010-11-02
Port forward external 80 to port 80 on the Ubuntu server.
Port forward external 81 to port 80 on the Windows server.
Instruct your email users to use xyz.com:81/exchange when accessing from outside.

EDIT: You could also set up a standard redirect on the Ubuntu server's /exchange URL to automatically forward anyone who uses the old address.

---

### Post by Glencore on 2010-11-02
> **Ryan Dwyer said:**
> Port forward external 80 to port 80 on the Ubuntu server.
Port forward external 81 to port 80 on the Windows server.
Instruct your email users to use xyz.com:81/exchange when accessing from outside.

EDIT: You could also set up a standard redirect on the Ubuntu server's /exchange URL to automatically forward anyone who uses the old address.

Thank you for the advice. I will try this.

---

