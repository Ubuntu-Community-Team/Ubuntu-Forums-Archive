---
title: "disable remote login?"
date: 2006-02-02
forum: Server Platforms
---

### Post by slavik on 2006-02-02
just read the thread about a user finding 'checka'

how do I disable all remote login attempts to my system? (this is a laptop, so there is no reason for telnet/ssh and others)

---

### Post by encompass on 2006-02-02
if you don't use the software... I would just remove it... for instance open-ssh-server.... jsut remove the software and you shouldn't have any problems.  Also... you can restrict everything comming into your computer with your firewall... an easy way to work with your firewall is installing this...
> sudo apt-get install firestarter
that should do the trick.

---

### Post by slavik on 2006-02-02
well, my firewall (router) doesn't even respond to ping

but my laptop has wifi and I want to restrict it at the laptop level ...

how can I configure mysql server (I believe it is installed by default?) to deny any connection (not even ask for login) that comes from anything other than 127.0.0.1?

---

### Post by imagine on 2006-02-03
[QUOTE=slavik]well, my firewall (router) doesn't even respond to ping[/QUOTE]
Bad idea, ICMP is no superfluous protocol.
[http://www.hansenonline.net/Networking/stealth.html](http://www.hansenonline.net/Networking/stealth.html)

[QUOTE=slavik]but my laptop has wifi and I want to restrict it at the laptop level ...[/QUOTE]By default Ubuntu doesn't offer any services to the outside. So if you didn't install or enable anything you don't have to worry.

[QUOTE=slavik]how can I configure mysql server (I believe it is installed by default?)[/QUOTE]No, it's not installed by default.

---

