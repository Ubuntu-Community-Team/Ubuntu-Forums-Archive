---
title: "ubuntu thin client (LTSP) server"
date: 2015-03-12
forum: Server Platforms
---

### Post by Moofus on 2015-03-12
Hey! im new to using this forum, so tell me if i should be doing anything differently. but anyway, my school is thinking of getting a new LTSP network of thin clients (probably raspberry pis with Berry Terminal), and i dont know how big of a server, or more specifically processor, i would need. we will be running ubuntu server 14.04 and could have over 40 clients, at times most of them being used for google docs and web browsing mostly. the server might also be used for backups, or hosting a web site, im not really sure.  at where i work we have some old servers like a Poweredge 2900 and T310, would those work and still have some headroom?

---

### Post by Thirtysixway on 2015-03-19
> **Moofus said:**
> Hey! im new to using this forum, so tell me if i should be doing anything differently. but anyway, my school is thinking of getting a new LTSP network of thin clients (probably raspberry pis with Berry Terminal), and i dont know how big of a server, or more specifically processor, i would need. we will be running ubuntu server 14.04 and could have over 40 clients, at times most of them being used for google docs and web browsing mostly. the server might also be used for backups, or hosting a web site, im not really sure.  at where i work we have some old servers like a Poweredge 2900 and T310, would those work and still have some headroom?

I would checkout the edubuntu.org documentation on this

[https://edubuntu.org/documentation/12.04/installation-guide](https://edubuntu.org/documentation/12.04/installation-guide)

They recommend ~4GB per 20 clients. Personally I'd look at probably more than that as it can't hurt.  RAM and Network IO will probably be your bottle neck for just web browsing, google docs, that sort of thing.  I would get probably 4x1Gb network connections and use lacp/bonding to create a 4Gb connection out to the clients. Though this also entirely depends on your network topology. And then probably a dedicated uplink to support internet browsing.

I would NOT plan on using the same server for backups or webhosting.  Ignoring the security, single point of failure, etc, your server is going to be busy with 40 clients :)

---

### Post by ramesh24 on 2016-03-05
Have a look into this 
[http://wiki.ltsp.org/wiki/Installation](http://wiki.ltsp.org/wiki/Installation)

---

### Post by ramesh24 on 2016-03-05
Complete help guides available here
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

