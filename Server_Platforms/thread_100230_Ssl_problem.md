---
title: "Ssl problem?"
date: 2005-12-07
forum: Server Platforms
---

### Post by olat on 2005-12-07
Im runnig ubuntu breezy as a webserver. I´ve enabled ssl on the webserver and it has worked perfekt until today. I get a wierd errormessage with firefox:

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

I know that this is not a lot of info but I dont know what you need to know. Can anybody help me?

- olat

---

### Post by drogoh on 2005-12-07
[QUOTE=olat]
Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.
[/quote]

That would mean you went to [http://site:443/](http://site:443/) instead of [https://site/](https://site/)

---

