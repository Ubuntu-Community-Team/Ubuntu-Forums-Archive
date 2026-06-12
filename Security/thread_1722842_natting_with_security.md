---
title: "natting with security"
date: 2011-04-06
forum: Security
---

### Post by shivaram on 2011-04-06
Hi,
 
I would like to do natting and dhcp server in the same server, i have done that by using a script MASQUERADESCRIPT.sh,  But when clients get ipaddress and gatway they are able to browse all websites but i would like to block some sites or group of websites. please help me on this. i am using Ubuntu Server 10.10. thanks in advance...

---

### Post by shivaram on 2011-04-06
:KSHi,
I have configured Nat and DHCP Server. My clients machines are taking Ip address, Subnet mask, gateway and dns. But they are able to access all websites. Now i would like to block some sites , how do i do that , please help me . Thanks in advance.

---

### Post by uRock on 2011-04-06
[OpenDNS]("http://www.opendns.com/")

---

### Post by cariboo on 2011-04-06
I merged you two threads, please don't create multiple threads on the same subject.

---

### Post by bodhi.zazen on 2011-04-06
With that setup, if you wish to do content filtering, I would suggest you add a proxy.

Squid + squidguard, dandguardian, privoxy.

Of the 3, IMO, privoxy is easiest to learn, but squid has more features (and is thus more complex to learn, the more features you use, the more complex squid becomes to use).

Dansguardian will piggyback with squid or privoxy. The default content filtering will need to be reviewed and perhaps modified, which is IMO more time consuming then privoxy.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

HTH.

---

