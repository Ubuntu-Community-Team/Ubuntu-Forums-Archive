---
title: "SASL killed my mail server!"
date: 2008-11-29
forum: Server Platforms
---

### Post by bluethundr on 2008-11-29
Hey guys, 

 I tried installing sasl onto my postfix configuration. ever since then, I am unable to telnet to my mail server on port 25. it connects but it immediately closes the connection. 

however, I am able to telnet to port 110 and test out my pop server and THAT WORKS!

 Can someone offer some troubleshooting tips?

---

### Post by MJN on 2008-11-29
A few things: check your mail logs, try removing the SASL configuration from Postfix, post your Postfix config.

Mathew

---

