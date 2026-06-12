---
title: "Managing OpenVPN users"
date: 2010-12-23
forum: Server Platforms
---

### Post by Frodaddy on 2010-12-23
I currently am running 
1. x86_64 GNU/Linux Ubuntu 10.04 LTS
2. OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] 

I am wondering if there was an easy way to manage resources (mainly bandwidth) based on the users connected. As far as mem/cpu it seems these aren't very intensive but I think top is sufficient. Also is it possible to see what users are logged in and authenticated? 

Any ideas?

---

### Post by kroon78 on 2010-12-23
Not sure if this is the answer to your question, but webmin would give you a gui to mess with openvpn and all its modules.

---

### Post by samosamo on 2010-12-24
are you familiar with the concept of bandwidth shaping?  aka QoS?  not sure if it's available on tun/tap interfaces but you could check it out

---

### Post by Frodaddy on 2010-12-29
> **samosamo said:**
> are you familiar with the concept of bandwidth shaping?  aka QoS?  not sure if it's available on tun/tap interfaces but you could check it out
Yes, I'm familiar with QoS, but AFAIK it's usually done at the hardware/firmware level of the router.

I don't necessarily need to tune QoS parameters, but rather I'd like to just know if there is a bandwidth problem (so like user X is using 2Mbit/s and user Y is using 2Mbit/s). Maybe it's not even an issue for me, just being proactive.

---

### Post by Frodaddy on 2010-12-29
> **kroon78 said:**
> Not sure if this is the answer to your question, but webmin would give you a gui to mess with openvpn and all its modules.

So this?
[http://www.webmin.com/cgi-bin/search_third.cgi?search=openvpn](http://www.webmin.com/cgi-bin/search_third.cgi?search=openvpn)

Doesn't seem to be supported very well =/

---

### Post by Skadork on 2011-01-06
> **Frodaddy said:**
> So this?
[http://www.webmin.com/cgi-bin/search_third.cgi?search=openvpn](http://www.webmin.com/cgi-bin/search_third.cgi?search=openvpn)

Doesn't seem to be supported very well =/


It is pretty intuitive to use.  I use it on 3 different ubuntu servers and it works very well.  I love that it will export everything needed for the client cause I can just zip it up, email it to the user and they unzip it, restart the client and it works...

---

