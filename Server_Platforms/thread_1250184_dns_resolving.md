---
title: "dns resolving"
date: 2009-08-26
forum: Server Platforms
---

### Post by bokiv_mkd on 2009-08-26
Hi , 
i just installed Ubuntu-server 9.04, everything is fine except DNS resolving. i install bing9 (i will use as a caching only server) , when i try to test it with " dig domain.com it resolve. But when i try to resolve from another computer in my network it couldn't.

here is my named.conf.option :

dns6@DNS6:/etc/bind$ more named.conf.options
options {
directory "/var/cache/bind";

// If there is a firewall between you and nameservers you want
// to talk to, you may need to fix the firewall to allow multiple
// ports to talk. See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

// If your ISP provided one or more IP addresses for stable
// nameservers, you probably want to use them as forwarders.
// Uncomment the following block, and insert the addresses replacing
// the all-0's placeholder.

// forwarders {
// 0.0.0.0;
// };
max-ncache-ttl 1000;
max-cache-ttl 1000;
max-cache-size 150m;
recursive-clients 4000;
notify no;
cleaning-interval 60;
recursion yes;
auth-nxdomain no; # conform to RFC1035
listen-on-v6 { any; };
};

Also i try to use port scanner to see if port 53 is open, that is ok. 

Can anyone help me solving this problem.

---

### Post by rybl on 2009-08-28
Are you sure the other machine is using your DNS server as its primary DNS?

---

### Post by bokiv_mkd on 2009-08-31
Yes,  the same ip i use for other server and it work, when i unplug and put on my new server (ubuntu) it doesn't work. It seems like some process or some local firewall on Ubuntu blocks queries from outside. Should i enable or disable some of the processes on server??

---

