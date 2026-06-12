---
title: "newbie to servers"
date: 2008-01-24
forum: Server Platforms
---

### Post by NapsterX on 2008-01-24
i was wanting to add a server to my xubuntu desktop i was wondering what kind of packages i need and if anyone could point me in the right direction to finding a beginners guide

---

### Post by mssever on 2008-01-24
What kind of server do you want? It's as simple as installing the appropriate server and configuring it, but since there are so many different kinds of servers, it's impossible to help you furher without more information.

---

### Post by NapsterX on 2008-01-24
i'm looking for a server to share files over the web

---

### Post by HermanAB on 2008-01-25
Over the web...

I'd suggest SSH, since it is encrypted, though what you would likely be more familiar with is FTP, so install proftpd.  It works right out of the box.  Don't configure anything, since you'll likely break it, just install it and run it and gain some experience before you try to change anything.

Cheers,

Herman

---

### Post by mssever on 2008-01-25
> **HermanAB said:**
> Over the web...

I'd suggest SSH, since it is encrypted, though what you would likely be more familiar with is FTP, so install proftpd.
While SSH and FTP operate over a network, neither operates over the web. For the web, you need a web server, such as apache2 or lighttpd. I don't know if the OP understands the distinction I've just made between a network (such as the Internet) and the web, but such a distinction does matter when you're trying to communicate what type of server you're looking for.

---

### Post by The Cog on 2008-01-25
> **mssever said:**
> While SSH and FTP operate over a network, neither operates over the web. For the web, you need a web server,....
I agree, bit I think NapsterX was probably using "web" and simplly meaning "internet". If so, I also recommend using an SSH server. 

If using HTTP really is a requirement, then a web sever like apache will have to be the basis.

---

