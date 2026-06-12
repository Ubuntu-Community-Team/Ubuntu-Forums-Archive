---
title: "Server Startup Screen"
date: 2008-10-20
forum: Server Platforms
---

### Post by champishere on 2008-10-20
Does anyone know if the messages, when the server is turn on, are logged to a file on the system?

For example the screen at the beginning that says what is starting:
* Starting Postfix Mail Transport Agent postfix
* Starting deferred execution scheduler atd
* Starting periodiccommand scheduler crond
* Starting web server apache2
* Running local boot scripts (/etc/rc.local)


I've been having some hard drive problems lately but I haven't been able to see what happens after startup because I use ssh to access this computer.

Is there a file that this info is logged to?

---

### Post by HermanAB on 2008-10-20
For a running commentary:
sudo tail -f /var/log/messages

or
sudo dmesg|less

Cheers,

Herman

---

