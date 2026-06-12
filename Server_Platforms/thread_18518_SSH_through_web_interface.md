---
title: "SSH through web interface"
date: 2005-03-07
forum: Server Platforms
---

### Post by thorN on 2005-03-07
Hi,

I'd like to be able to access my server (at home) from elsewhere, and so I've set up SSH. This works fine and is great.

However, a lot of places block all ports but 80 or don't have the SSH client.

is there a web interface for this? maybe running in PHP?

thanks

---

### Post by alastair on 2005-03-07
Mindterm? Not used it - it is Java :

[http://www.appgate.com/products/80_MindTerm/](http://www.appgate.com/products/80_MindTerm/)

Alternatively, so can be clever with ssh redirection perhaps.

---

### Post by thorN on 2005-03-08
[QUOTE=alastair]Mindterm? Not used it - it is Java :

[http://www.appgate.com/products/80_MindTerm/](http://www.appgate.com/products/80_MindTerm/)

Alternatively, so can be clever with ssh redirection perhaps.[/QUOTE]
 I got it running, but it wouldn't connect through port 80.

Do I need a httptunnel server? (It's in the repositories, which is nice :D)

---

### Post by dewey on 2005-03-08
I'm also very interested in this, I would love to connect through port 80 to my home computer from school, they have just started blocking all ports except 80, so now I can't even use webmin.  Tell me if you find anything of use please, preferably free.

---

### Post by johnny! on 2006-01-08
probably for some people interesting:
[http://dag.wieers.com/howto/ssh-http-tunneling/](http://dag.wieers.com/howto/ssh-http-tunneling/)

you would need an apache server that provides a ssh tunnel over http for you, so you could connect also in restricted networks.

the problem is, that only a java applet or similar client progs don't fit, because they go via port 22... i also would need a nice web interface but haven't found one yet that works serverside.

if someone knows, please post.

---

### Post by Suger on 2006-01-08
You might want to have a look at

[http://proxytunnel.sourceforge.net/](http://proxytunnel.sourceforge.net/)

also

---

### Post by imagine on 2006-01-08
PuTTY (Windows SSH-Client) doesn't require any installation. Just download and start.

Did you try moving your SSH-Server to Port 80? As long as the school's gateway doesn't sniff around in the traffic it will work.

Sometimes there's also a socks proxy which can be used.

---

