---
title: "www with domain name points to ip instead of site"
date: 2009-10-10
forum: Server Platforms
---

### Post by R.Bucky on 2009-10-10
I host multiple domains on my single true static ip using Apache VirtualHosts. I also have a domain index at my ip address ([http://24.18.97.111](http://24.18.97.111)). The problem is that when any of my domains have a www in front of them they point to my ip domain index. My DNS at my registrar has www pointed to my @ and so on. Any suggestions on configuring this so a visitor can visit [www.markimoore.com](www.markimoore.com) and [http://markimoore.com](http://markimoore.com) and reach the same page?

Ubuntu Server 8.04, BIND9

---

### Post by t3r0 on 2009-10-10
Hi,

Your are most likely missing a "ServerAlias" directive in your virtual host block.

eg.

```

<VirtualHost ....>
 ServerName domain.com
 ServerAlias www.domain.com
......

</VirtualHost>

```


- Tero

---

### Post by R.Bucky on 2009-10-10
Uggg. I hate it when the solution is so bloody simple. Thank you t3r0.

---

