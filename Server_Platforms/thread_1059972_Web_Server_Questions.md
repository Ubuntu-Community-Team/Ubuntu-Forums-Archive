---
title: "Web Server Questions"
date: 2009-02-04
forum: Server Platforms
---

### Post by chsmith700 on 2009-02-04
Hello,

Sorry if this has been posted before, however. I am setting up a server for a small website I am going to be building in the near future. Problem is, I got it working. I can load up the pages from inside my local network. I can also load up the pages from my 3G phone. However anywhere besides my phone or local network I am unable to access it.

I have LAMP (obviously) and shorewall installed.

Is there something blatently obvious I am missing here?

My router is configured for port forwarding for 80 and 22.
chsmith700 is online now Report Post   	Edit/Delete Message

---

### Post by Thirtysixway on 2009-02-04
Is shorewall blocking anything?  and double-check your IP [www.whatismyip.com](www.whatismyip.com)

---

### Post by Cerox Rex on 2009-02-04
I'f you dont have a static ip you also need a DDNS account. like [http://www.dyndns.com]("http://www.dyndns.com")

you also need an DynDNS Update Clients so DynDNS know where to route requests for your webserver.

---

### Post by chsmith700 on 2009-02-04
> **Cerox Rex said:**
> I'f you dont have a static ip you also need a DDNS account. like [http://www.dyndns.com]("http://www.dyndns.com")

you also need an DynDNS Update Clients so DynDNS know where to route requests for your webserver.

I will do this when I actually apply a domain name, for not I am just getting in thru the public IP address. I can still browse via my phone to it, and click links and what not. Still unable to do so from my computer outside of the local network there.

Verified IP address.

---

