---
title: "Server 8.10 64-bit with KDE"
date: 2009-03-06
forum: Server Platforms
---

### Post by snorkytheweasel on 2009-03-06
Opening remark: I have/manage several Linux boxes, mostly Ubuntu. On all of the other Ubuntu machines, everything works out of the box. On this 64-bit server with KDE, everything is a struggle. 

Today's snivel is that I can't ssh, telnet, or rlogin - using Putty - from Windows in to the server. The error messages, in sequence, are 
[FONT="Fixedsys"]Connection closed by remote host[/FONT]
Upon clicking "OK" I get
[FONT="Fixedsys"]Network error: connection refused[/FONT]

FWIW, this happens before Putty's session log kicks in.

All of my other 'nixes (including an ancient RedHat) happily greet me and let me in. No muss, no fuss, no decoder ring or magic wand. I simply select the connection type (SSH, telnet, rlogin), enter the IP, and click "Open"

I can run the server's webmin from any browser inside the network
I can connect to the server using Putty running on the server itself (makes a damn fine console)
I can ping the server from any computer in the network

I assume that it is configuration problem on the server. Where do I look for the magic incantation to make this work?

---

### Post by snorkytheweasel on 2009-03-06
Problem solved. It was a configuration issue.

But ... my 64 and I will be back.

---

### Post by gtdaqua on 2009-03-06
KDE is even more resource consuming than GNOME. But why do you want a desktop within a server?

---

