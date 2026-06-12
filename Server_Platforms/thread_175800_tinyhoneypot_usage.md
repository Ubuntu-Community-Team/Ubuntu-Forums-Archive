---
title: "tinyhoneypot usage?"
date: 2006-05-13
forum: Server Platforms
---

### Post by lukeblack on 2006-05-13
Hey guys,

I installed tinyhoneypot, and it seemed to go fine. When I run sudo thpot ftp for example, it creates the interface - but not a daemon. How exactly do I go about setting it up so when people connect to port 21 on my pc they are greeted with thpot's interface? Any advice would be much appreciated!

Many thanks in advance,
Luke :KS

---

### Post by lukeblack on 2006-05-13
-

---

### Post by jimmyridge on 2008-03-12
Leet@yourhost#cat /usr/share/doc/tinyhoneypot/examples/inetd.conf.sample

ftp     stream  tcp     nowait  thpot    /usr/sbin/thpot thpot ftp
smtp     stream  tcp     nowait  thpot    /usr/sbin/thpot thpot smtp
http     stream  tcp     nowait  thpot    /usr/sbin/thpot thpot http
pop3     stream  tcp     nowait  thpot    /usr/sbin/thpot thpot pop3
shell     stream  tcp     nowait  thpot    /usr/sbin/thpot thpot shell

Leet@yourhost#ls /usr/share/doc/tinyhoneypot/
changelog.Debian.gz  changelog.gz  copyright  examples  README.Debian  READTHIS.gz










google is my friend

---

### Post by jimmyridge on 2008-03-14
eh xinetd is better read the examples above for it i got it working but its a bit lame honeyd is way cooler

---

