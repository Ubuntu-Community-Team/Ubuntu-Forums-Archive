---
title: "Network traffic routing?"
date: 2014-06-14
forum: Server Platforms
---

### Post by ionbasa on 2014-06-14
Hello forum members!

I am looking into finding a solution to host multiple domain names on one IP address. Note: Apache Virtual Hosts won't cut the mustard as it only routes HTTP traffic?

I am looking into routing tcp/udp traffic to specific applications, like a sql server and to virtual machines. 

Will Iptables be able to do this properly?

My idea so far is that I can setup 2 virtual network adapters and then have iptables route traffic to those 2 adapters. I could then have my applications bind to those adapter.

Is there a better or more elegant solution to this problem?

---

### Post by elico on 2014-06-15
For each protocol you will need a differet proxy.
In most cases it's being used only for http and if needed something like sql you just use another db name and there for there is no need for different servers.
For what you want you will need a very complex proxy server unless you will use different port for each service which is meant for other domain\client.
You have about 60k ports .. use them as you will since I do not know about a proxy that will fit all of your services.

---

### Post by ionbasa on 2014-06-15
> **elico said:**
> ...
You have about 60k ports .. use them as you will since I do not know about a proxy that will fit all of your services.
I was trying to avoid different ports though :(

Someone on server fault suggested using HE ipv6 broker service, and giving each VM dedicated IPv6, which will work, but only for IPv6 aware software.

---

### Post by SeijiSensei on 2014-06-18
Maybe you should explain why you are doing this?

Are you trying to limit inbound traffic over IP1 to a set of permitted services that differs from those allowed over IP2?  If so, then iptables would work for this.

```

/sbin/iptables -A INPUT -d 10.10.10.10 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -A INPUT -d 10.10.10.11 -p tcp --dport 5432 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

```

That would accept HTTP connections to 10.10.10.10 and PostgreSQL connections to 10.10.10.11.  All other traffic is blocked.  Functionally, though, having the second interface is fairly superfluous if both services are running on the same box.

If you want to use this box as a proxy supporting other servers behind it, then you could use

```

/sbin/iptables -A INPUT -d 10.10.10.10 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -d 10.10.10.10 -p tcp --dport 80 -j DNAT --to-destination 10.100.100.100:80
/sbin/iptables -A FORWARD -d 10.10.10.10 -p tcp --dport 80 j ACCEPT 
/sbin/iptables -A INPUT -d 10.10.10.11 -p tcp --dport 5432 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

```

This accepts inbound traffic on 10.10.10.10:80 and redirects it to 10.100.100.100:80.  You will also need to enable IPv4 packet forwarding in /etc/sysctl.conf.

---

### Post by The Cog on 2014-06-18
I think what you are trying to do is not possible without using differing port numbers. In general, the only information available to route an incoming connection is the destination IP address and port number. You have already said there is only one IP address available, so the routing must be done based on the destination port number. 

Applications have their own "well known" port numbers, such as 22 for SSH. If only one of the hosts is to offer a service, this is easy - just forward that port to that host. If multiple hosts are to offer the same service, then you have no choice but to use non-standard ports. This can be done with destination network address translation (DNAT) in iptables. It may have trouble with SSH though - I think SSH keeps a record of IP address and fingerprint, and probably won't like seeing different identities on the same IP address at different times.

I can think of two exceptions to the above:

* Protocols such as HTTP which are designed to carry extra information about which host they want, inside of the network protocol - desightd for use with proxies.

* If you know for sure that certain clients (by IP address) will only ever want to talk to one of the two virtual hosts, you can use extra rules such that client X is always forwarded to host Y.

---

