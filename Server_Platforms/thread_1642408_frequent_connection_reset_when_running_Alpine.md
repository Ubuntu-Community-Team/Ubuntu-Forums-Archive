---
title: "frequent connection reset when running Alpine"
date: 2010-12-10
forum: Server Platforms
---

### Post by scalyanteater on 2010-12-10
I'm running Ubuntu 10.04.1 (2.6.32-26-server) things are generally going smoothly. But I find that when running the email client Alpine v. 2.00 over an ssh connection, it is frequently dropped with the message "connection reset by peer".

Alpine is accessing the gmail smtp server. Resets of this kind are rare with any other application, and when Alpine is run directly on the server itself, it seems quite stable, and is rarely closed out of the gmail server.

I tried adding "ServerAliveInterval" and "ServerAliveCountMax" lines to ssh_config, but it seems to have no obvious effect.

Can anyone suggest reasons for the instability of the connection, or possible fixes?

Many thanks!

---

