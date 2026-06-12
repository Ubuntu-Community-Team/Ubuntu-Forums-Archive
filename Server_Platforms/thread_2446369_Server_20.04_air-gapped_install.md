---
title: "Server 20.04 air-gapped install"
date: 2020-06-29
forum: Server Platforms
---

### Post by tps-mail on 2020-06-29
I maintain hundreds of servers which are air-gapped. They are physically unable to connect to the internet. This has been working fine since 12.04 when I started this. I can move updated .deb files by hand and rebuild the local repository. I can boot from CD and install new servers. Until 20.04. It seems like the 'live' CD means you need a 'live' internet connection.

Does this mean from 20.04 on, I have to use another distribution? Fedora is the next best option for me, but with my Debian background, switching flavors will be painful, along with having to refactor all the packages we have custom built. I know there's the alternate image for the next few months, but, I'm playing the long game, which is why I went with a Debian based solution initially.

---

### Post by TheFu on 2020-06-29
Fedora isn't a server. it is a desktop and not "supported" - look at CentOS.

---

### Post by LHammonds on 2020-06-30
Have you tried to create an [autoinstall CD](https://ubuntu.com/server/docs/install/autoinstall)?

LHammonds

---

