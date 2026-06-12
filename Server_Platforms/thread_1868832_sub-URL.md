---
title: "sub-URL"
date: 2011-10-24
forum: Server Platforms
---

### Post by Justinba1010 on 2011-10-24
I wanted to know, I want to have 3 servers. And them all to be connected in 1 url. In sub-URL. Like: suburl.mymainurl.com
First is it possible? And if anyone can give me a brief on how I would do it, that would be great.

---

### Post by volkswagner on 2011-10-24
It is possible, but you need to provide more details.

Is this for LAN only?

How many public IP addresses do you have (if this is for WAN)?

You'll likely need to setup on server as a reverse proxy to the others, if you have only one IP getting port 80 forwarded to.

PS: the term you are looking for is subDomain not subUrl...

---

