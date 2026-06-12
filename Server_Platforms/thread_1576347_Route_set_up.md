---
title: "Route set up"
date: 2010-09-17
forum: Server Platforms
---

### Post by liuhb86 on 2010-09-17
There are two connections in my Ubuntu server:

eth0 is a normal interface and,
eth1 is configured with an static IP, and has an domain name with that  IP. But this connection is charged by bytes, very expensive.

My question is how to set up the route table so that:

everyone can access my server with the domain name, and
let the traffic goes from eth0 as much as possible(I have a proxy service on my server.
At least, let the proxy traffic goes from eth0)?

My current route is:
x.x.81.0    *               255.255.255.0   U     0      0        0 eth1
x.x.81.0    *               255.255.255.0   U     0      0        0 eth0
default         x.x.81.1    0.0.0.0         UG    100    0        0 eth0
default         x.x.81.1    0.0.0.0         UG    100    0        0 eth1

, which made the server inaccessible from outside by hostname.

---

### Post by byStanderone on 2010-09-17
...first you'd have to gain access to the router's setup interface, you have to know the default address ofyour router...usually provided in your router's manual and infos. just type in that address on your browser (ex. firefox) and you'll be presented the setup page for that router, assuming that you are the admin and that you know the password and name required to open the setup page.

---

### Post by HermanAB on 2010-09-17
Howdy,

You should read the Advanced Routing Howto on tldp.org

---

### Post by liuhb86 on 2010-09-17
I don't think I have a router. The net card have two interfaces.
The subnet router(x.x.81.1) is out of my control.

---

### Post by liuhb86 on 2010-09-17
Thanks, I'll read it.
> **HermanAB said:**
> Howdy,

You should read the Advanced Routing Howto on tldp.org

---

### Post by koenn on 2010-09-17
Read up on routing is always a good idea when you're planning to play with networks.

However, what you're trying to do is really messing with TCP/IP

If you want connections coming in on eth1 (because it has a domain name), the normal course of action is that the replies to does connections also go out eth1. But you don't want that because it costs money. 

You can probably make it so that traffic goes out eth0, but that will be confusing to the clients because they'll expect it to come from (the ip address of) eth1. Furthermore, they might see it as a new connection coming in, and even worse, a new connection without SYN flag set - even if those are not dropped by a firewall, your TCP handshake will most likely not work. 

You might be able to pull this off with iptables, ie route or redirect all traffic out eth0, and masquerade eth0 with the ip address of eth1.

---

### Post by liuhb86 on 2010-09-19
> **koenn said:**
> 
If you want connections coming in on eth1 (because it has a domain name), the normal course of action is that the replies to does connections also go out eth1. But you don't want that because it costs money. 


Now, I can accept some traffic through eth1. It is OK for www, ssh and mail serivces going from eth1.  So I did 'route del default eth0'.
But I also have a proxy service which generate a lot of traffic to fetch pages for proxy users. 
So now, my only wish is to let the squid proxy service fetch pages through eth0. Other traffic can go either from eth0 or eth1. It doesn't matter.

Is it easier?

I changed the tcp_outgoing address in squid.conf but it doesn't work.

If this cannot be solved, I'll set up another server to run the proxy separaterly:)

---

### Post by koenn on 2010-09-19
as such, redirecting and masquerading only "proxy" traffic is not easier or more difficult than redirecting and masquerading all traffic. but it probably reduces the risk for "unexpected problems" on non-web/proxy connections. 


squid tcp_outgoing_address should work, but it will require a working route for the given address. say you tell squid that it should use address 123.123.123.123, your network stack will still need to know how 123.123.123.123 connects to whatever webserver squid needs to fetch a page from; this means you'll need a route from 123.123.123.123 to "the internet", but if you use "default route" to accomplish this, this default  might also apply to other traffic, and mess things up. 
Here's were "advanced routing" might help, eg if you can specify a "next hop" from 123.123.123.123 to a router that has internet access, and let that router figure it out further, this might work. 


also, you may need moere than one tcp_outgoing_address statement, and need to check some other settings in squid.conf, because the may be incompatible - here are some examples
 [http://www.squid-cache.org/Doc/config/tcp_outgoing_address/](http://www.squid-cache.org/Doc/config/tcp_outgoing_address/)


a separate proxy server is probably easier :)



----
disclaimer : never done any of this; just (educated ? ) guesses. You might want to just give it a try and tweak it till it works.

---

