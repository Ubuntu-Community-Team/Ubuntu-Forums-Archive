---
title: "Limit upload speed"
date: 2012-02-29
forum: Server Platforms
---

### Post by _Wolverine_ on 2012-02-29
I have installed ubuntu server and configured everything (dns,dhcp,samba,squid...)

But i would like to limit the upload speed of my network

internet ----> eth0 server eth1 <----> clients

any ideas?

---

### Post by nsnidanko on 2012-03-01
You should look into **tc tool** (traffic control). Here's some info:

[http://linux-ip.net/articles/Traffic-Control-HOWTO/](http://linux-ip.net/articles/Traffic-Control-HOWTO/)
[http://atmail.com/kb/2009/throttling-bandwidth/](http://atmail.com/kb/2009/throttling-bandwidth/)

If you google around for keywords above you should find more info.

Hope it helps,
Naz

---

### Post by _Wolverine_ on 2012-03-01
will look into it
ty

edit: F*CKING THANK YOU!!!!!!
had some problems when recompiling the kernel (eth0 becames eth2 but i fixed it)
thanks a lot man!!!

---

