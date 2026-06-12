---
title: "ip/domain redirects to router"
date: 2007-11-26
forum: Server Platforms
---

### Post by briansvgs on 2007-11-26
I have set up a web server using ubuntu gutsy server. I got port forwarding and everything set up in the router, and registered a free domain with dyndns. The website can be accessed with either of these addresses from the internet, but when I try to access it from inside of the network using either address, it redirects to the router. I tried shutting down the server, and it still happens, so I know that it isn't a server problem. Does anyone know how to fix this?

Thanks,
Brian

---

### Post by rickyjones on 2007-11-26
Most likely a DNS issue. Your internal client asks the router who xxx is. The router doesn't know so it asks someone else. This server says it is xxx.xxx.xxx.xxx, which just so happens to be your IP address. So the router displays itself to you. Note, I've never had this happen on my own networks, but the router brand could make the difference here.

A possible solution would be to add a mapping to your hosts file. E.g.: xxx.com 192.168.1.1

Of course you'd want to use your own internal IPs and your domain name.

-Richard

---

### Post by briansvgs on 2007-11-26
There are several computers on my network, not all of which are mine, so I was hoping to find a solution that didn't involve modifying the hosts file.Its an actiontec dsl router. It had sounded to me like the router recognizes that the ip is its external ip address, but doesn't realize that it is supposed to forward port 80 for the external ip to the server.

---

### Post by koenn on 2007-11-26
> **briansvgs said:**
> There are several computers on my network, not all of which are mine, so I was hoping to find a solution that didn't involve modifying the hosts file.Its an actiontec dsl router. It had sounded to me like the router recognizes that the ip is its external ip address, but doesn't realize that it is supposed to forward port 80 for the external ip to the server.
maybe the router is aware that the connection comes through its LAN interface and finds it unnecessary to port-forward it back to where it came from ... I don't quite see how to fix that, unless the router itself offers options that deal with this sort of situation. 

The suggested workaround with the hosts file, or something similar on a DNS server if there is one on the LAN and you control it, is the only solution I see.

---

### Post by MJN on 2007-11-27
Agreed - many home routers don't support so-called 'NAT loopback'. Post the make/model and I'm sure we can find out if yours does (or not).
 
Mathew

---

