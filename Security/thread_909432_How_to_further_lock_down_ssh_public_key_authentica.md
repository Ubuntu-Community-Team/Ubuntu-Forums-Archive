---
title: "How to further lock down ssh public key authentication"
date: 2008-09-03
forum: Security
---

### Post by moonpup on 2008-09-03
Hi eveyone,

Here's a link that admins may find very beneficial when using ssh public key authentication. I was not aware of these options as I only recently came across them when my job required me to figure out a way to restrict access.

Basically you can create ssh keys, to only perform a specific task (beneficial to scripting) and immediately log out, to limiting key authentication from specific hosts, to not opening a shell etc... Give it a read and I'm pretty sure you will find it enlightening and useful!

[http://www.sun.com/bigadmin/features/articles/sec_shell_2.html](http://www.sun.com/bigadmin/features/articles/sec_shell_2.html)

---

### Post by kevdog on 2008-09-06
Might want to check out the tool fwknop and read about port knockers (fwknop is a single packet port knocker authentication program) if you really want to harden your ssh application.  Use of a firewall will also harden the application.

---

