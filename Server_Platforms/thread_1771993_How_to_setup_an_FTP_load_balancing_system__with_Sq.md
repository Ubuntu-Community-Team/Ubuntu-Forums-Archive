---
title: "How to setup an FTP load balancing system  with Squid"
date: 2011-05-31
forum: Server Platforms
---

### Post by ducviet_hutech on 2011-05-31
Hi all,
I'm a newbie on Ubuntu, I have a problem with squid proxy.
I'd like to configure a system, include: 
- a server is named ProxyServer that is installed Squid proxy.
- three servers, are named FTPServer01, FTPServer02, FTPServer03. each server is installed vsftpd. 
- Clients are installed Filezilla to up/download resource.
All servers are managed by IP address.
When a client request a resource, client connect to ProxyServer, this ProxyServer will switch to one of Ftp servers.
I do not know how to configure the squid's config file to setup them.
Pls help me step by step to.
Thank so much !
The system I'd like is showed bellow:
[IMG]http://www.uphinhnhanh.com/images/30ProxyServerSystem.png[/IMG]

---

### Post by rosenkavalier on 2011-05-31
[FONT="Comic Sans MS"][COLOR="Blue"]ah, I think squid is useful for caching request, storing static contents from a website to be delivered to several accessing clients...

maybe for this purpose you can try round-robin DNS....? maybe tc could do the work...?

I hope [this page]("http://lartc.org") will help you

good luck :popcorn:[/COLOR][/FONT]

---

### Post by ducviet_hutech on 2011-06-02
> **rosenkavalier said:**
> [FONT=Comic Sans MS][COLOR=Blue]ah, I think squid is useful for caching request, storing static contents from a website to be delivered to several accessing clients...

maybe for this purpose you can try round-robin DNS....? maybe tc could do the work...?

I hope [this page]("http://lartc.org") will help you

good luck :popcorn:[/COLOR][/FONT]
Thanks Rosenkavalier!
I know it is useful for as you said but I'd like to setup them for my lap. :( The page you gave support me so much.

---

### Post by HermanAB on 2011-06-02
+1 for round robin DNS.

Keep it simple.

---

