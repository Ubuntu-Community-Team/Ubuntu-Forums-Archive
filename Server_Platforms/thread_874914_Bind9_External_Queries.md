---
title: "Bind9 External Queries"
date: 2008-07-30
forum: Server Platforms
---

### Post by metradynamix on 2008-07-30
Any help on this would be greatly appreciated. I was never able to accomplish this and I cannot find the answer to my problem.

I have setup Under Ubuntu Bind9 and was able before to make this DNS Server functional to the extent of managing some of my own Domains.

What I am attempting to do now is use Ubuntu 8.04LTS Server 32bit. I have installed Ubuntu and installed Bind9. I configured it to the best of my abilities and if I attempt to ping a domain name or dig a domain everything seems to be functional. That is with having set /etc/resolv.conf with the IP address of that server. 

That server is a Dedicated Server, which I want to use only for DNS. It has it's dedicated IP Address and there are no routers blocking ports.

When I go now on my home computer for example and now set in Windows XP DNS; with the IP of that DNS Server - which is not on the same network, but accessible via the Internet it refuses to function.

On the XP Machine doing a nslookup google.com returns:

*** Can't find server name for address ADDRESSOFDNSSERVER: Query Refused
*** Default servers are not available
Server: Uknown
Address: ADDRESSOFDNSSERVER

*** Uknown can't find google.com: Query Refused

I did setup Forwarders and used Public DNS Servers in my config.

I am completely stomped by this problem. I never succeeded in making a DNS Server with Ubuntu which accepted Queries directly externally.

Any help would be greatly appreciated.

---

### Post by RealPSL on 2008-08-16
I cannot be sure if this is your problem as I am not sure what the default value is anymore. However you might want to look at explicitly allowing queries from your source address space using [allow-query]("http://www.zytrax.com/books/dns/ch7/queries.html").

---

