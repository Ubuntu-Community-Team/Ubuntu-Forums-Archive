---
title: "OpenSSH reverse lookup using /etc/hosts before nameserver?"
date: 2010-04-06
forum: Server Platforms
---

### Post by dmrazor on 2010-04-06
Hi,

Like many others I'm running into some reverse lookup issues with SSH. Setup is as follows:

localnet setup
myserver - 192.168.0.x
myworkstation - 192.168.0.y

internet setup
84.162.xx.yy                A   myserver.mydomain.com
yy.xx.162.84.in-addr.arpa   PTR myserver.mydomain.com.

nslookup tests show that my reverse lookup is functioning correctly. However, if I use "myworkstation" to connect to myserver.mydomain.com using an external nameserver SSH says: "Address 84.162.xx.yy maps to myserver.mydomain.com, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!"

On myserver the /etc/hosts has the internal address for the server which seems the normal way to go to me. Changing this to the servers external address solves the issue. 

Apparently a connection originating from myworkstation arrives from/with my external address, and when its reverse is checked by the server it apparently finds its own internal address for that name in /etc/hosts before doing a nameserver query and thus concludes that internaladdress <> externaladdress which gives the error.

Is there any way to have the server check external DNS before /etc/hosts? Another solution would probably be running an internal DNS, so myworkstation doesn't connect through the 'outside'.

Thanks for any tips, comments.

Raz.

---

### Post by dmrazor on 2010-04-06
Never mind. Found the answer myself with some further searching. For those that might seek something similar, I set:

/etc/nsswitch.conf:
hosts:          mdns4_minimal [NOTFOUND=return] dns mdns4 files

/etc/host.conf:
order bind,hosts

Now DNS is used before /etc/hosts

Cya,

Raz.

---

