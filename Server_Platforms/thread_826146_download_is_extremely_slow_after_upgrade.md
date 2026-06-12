---
title: "download is extremely slow after upgrade"
date: 2008-06-11
forum: Server Platforms
---

### Post by alixixi on 2008-06-11
have been running 6.10 for a while until decided to upgrade to 8.10, i did a complete new install but after installation the download has become VERY slow, I'm trying to wget the apache tomcat it takes about 20seconds from other servers on the network running 6.10 but cannot finish downloading from 8.10

I disabled ipv6 like some people suggested by adding it to the /etc/modprob.d/blacklist (and lsmod shows its not there any more) but the problem is still there - any help is greatly appreciated 

Im running it on 64x Dell server with Broadcom III Ethernet card

thanks a lot

---

### Post by molotov00 on 2008-06-11
This isn't the first time I've seen this on the forums. I just did a quick look for the bug report but couldn't find it.

It's not just you though...

---

