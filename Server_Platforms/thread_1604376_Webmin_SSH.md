---
title: "Webmin SSH"
date: 2010-10-23
forum: Server Platforms
---

### Post by hantechbl on 2010-10-23
I am having problems with my ssh login screen, it says it's online when the login pops up and then when I've entered my name and password it says offline, why?  I am running webmin 1.520

---

### Post by HermanAB on 2010-10-24
$ ssh -vvv user@server

---

### Post by nicolasdiogo on 2010-10-24
if you are trying to access it from a remote location then check if there is a firewall blocking ssh.
that is a java pluggin that works the same way as Putty by openning a connection to port 22 by default.

---

