---
title: "DNS servers"
date: 2012-07-31
forum: Server Platforms
---

### Post by nikibg on 2012-07-31
how to save my dns servers in /etc/resolv.conf file  after restart ?

---

### Post by darkod on 2012-07-31
Usually in ubuntu server you don't enter dns servers directly in /etc/resolv.conf, especially in the latest 12.04 LTS version. Instead, you enter them in /etc/network/interfaces adding a line under the main interface:
dns-nameservers x.x.x.x y.y.y.y

So it would be like:
auto eth0
iface eth0 inet static
......
......
dns-nameservers x.x.x.x y.y.y.y

---

### Post by nikibg on 2012-07-31
10x man its work :KS

---

