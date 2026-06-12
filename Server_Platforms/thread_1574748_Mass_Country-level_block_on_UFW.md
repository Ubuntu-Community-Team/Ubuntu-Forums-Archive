---
title: "Mass Country-level block on UFW"
date: 2010-09-14
forum: Server Platforms
---

### Post by Richard1979 on 2010-09-14
The following before.rules file will block all connections from:


[LIST]
[*]Korea
[*]China
[*]India
[*]Russia
[*]Turkey
[*]Vietnam
[*]Ukraine
[*]Brazil
[*]Venezuela
[*]Pakistan
[/LIST]
Place it in /etc/ufw/ then do "ufw reload" to take effect.

Download it here:
[http://www.digit4l.net/linux/before.rules](http://www.digit4l.net/linux/before.rules)

Hopefully somebody finds it useful.

Networks are taken from [http://www.countryipblocks.net](http://www.countryipblocks.net)

---

### Post by LightningCrash on 2010-09-20
Something similar here for Cisco + etc on Sinokorea ranges
[http://www.okean.com/thegoods.html](http://www.okean.com/thegoods.html)

---

### Post by terazen on 2010-09-20
Wow the ipv6 version of this will probably be a tad smaller file. :-)

---

### Post by LightningCrash on 2010-09-20
If you install the GeoIP iptables module you can actually do that in a couple of lines.

[http://www.debian-administration.org/articles/518](http://www.debian-administration.org/articles/518)


That's for Debian but I'm sure it would work on Ubuntu with only a few modifications.

---

