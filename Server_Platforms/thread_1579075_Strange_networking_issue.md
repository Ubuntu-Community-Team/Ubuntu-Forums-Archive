---
title: "Strange networking issue"
date: 2010-09-21
forum: Server Platforms
---

### Post by Azdour on 2010-09-21
Hi all,

I have a machine (lets called it machine 1) with two networks card, eth0 and eth1. Both have static IPs. Once in a while the machine refuses to give access to the Internet via Firefox (eth0 is the route to router). Other machines on the network have no problems accessing the Internet. Eventually the machine would just magically start working again, but this time it just seems to have stayed broken.

I've done some simple diagnostics and found:

a) I have another machine running Apache with a Wiki on our network - [http://192.168.1.73:8084](http://192.168.1.73:8084). Machine 1 is unable to connect to this Wiki. I get 'the connection has timed out'. I can ping 192.168.1.73 and it responds in the usual fashion.

b) If I try to ping [www.google.com](www.google.com) it times out with:
ping: unknown host [www.google.com](www.google.com). I can ping google using its IP address.

c) On machine 1 I have tried traceroute on both [www.google.com](www.google.com) and its IP and I just get:

1 * * *
2 * * *

And so on until hop 30. Doing this on any other machine on the network works.

So while it seems I can ping internally in our network and outside, but when it attempts anything traceroute or URL related it does not work.

I would greatly appreciate any other things I could do to track this issue down, even if its to give more information.

Thanks.

---

### Post by endotherm on 2010-09-21
sounds like it could be name resolution. do you have DNS servers or do you point to a service providers?

try running this command from machine1
```
nslookup ubuntuforums.org
```

and what is the output of 
```
cat /etc/resolv.conf
```

---

### Post by Azdour on 2010-09-21
Hi,

Thanks for the quick reply.

The nslookup just times out with:

;; connection timed out; no servers could be reached

The resolv.conf just contains:

```
nameserver 192.168.1.254
```

Thats our router. The resolv.conf file looks the same as the other machines that work.

---

### Post by pricetech on 2010-09-21
What's the subnet of the second NIC ??

---

### Post by Azdour on 2010-09-22
The subnet for eth1 is 192.168.6.0

---

### Post by withjigs on 2010-09-22
When I had similar issues, I found that my default gateway wasn't setup correctly.

---

### Post by HermanAB on 2010-09-23
$ sudo route

Check the default gateway setting and fix it with something like this:
$ sudo route add default gw 192.168.1.1 eth0

Then fix your DHCP server and client with the correct information, so it won't go wrong again in a few hours.

---

### Post by pricetech on 2010-09-23
ETH1 should have no default gateway, or a default gateway of 0.0.0.0

---

