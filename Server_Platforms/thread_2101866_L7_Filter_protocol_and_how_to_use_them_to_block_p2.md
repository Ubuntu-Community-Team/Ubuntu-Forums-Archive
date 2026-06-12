---
title: "L7 Filter protocol and how to use them to block p2p"
date: 2013-01-05
forum: Server Platforms
---

### Post by Muk on 2013-01-05
I know the HOWTO says don't use L7 to block p2p:[http://l7-filter.sourceforge.net/HOWTO-userspace#Useful](http://l7-filter.sourceforge.net/HOWTO-userspace#Useful)

but on multiple search on google I see L7 on the top list to use for blocking p2p.

I followed this youtube guide to install L7 filter: [http://www.youtube.com/watch?v=VyxvIUCWV7w](http://www.youtube.com/watch?v=VyxvIUCWV7w)

and my /etc/l7.conf looks like this:
```


gnutella       3
imap            4
aim             5
smtp            6
dns             7
validcertssl    8
tor             9
ipp             10
ssdp            11
telnet          12
zmaap           13
yahoo           14
msnmessenger    15
ssl             16
ssh             17
http            18
#======================P2P=====================================
100bao          19
ares            20
bittorent       21
xunlei          22

```

i tried running xunlei and it works just like normal without any hinderance.

how do i tell L7 to start dropping bandwidth or block it completely?

---

