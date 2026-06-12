---
title: "Bind: ANAME to server 2 not forwarding externally"
date: 2010-12-08
forum: Server Platforms
---

### Post by R.Bucky on 2010-12-08
I have 2 servers operating on my home network. One server hosts Bind9 and a few web sites. The other is an Ubuntu repo mirror that I recently configured (10.1.10.26). Inside my network, requests to the olyubuntu.nwlinux domain function as it should. However, external requests do not get forwarded. Instead, they end up at my DNS box at 10.1.10.25. Again, internal requests are forwarded correctly.

Any red flags pop-up as to why this is occurring? Firewalls are not an issue.

```
$ORIGIN nwlinux.com.
$TTL 86400
@       IN      SOA     dns1.nwlinux.com. hostmaster.nwlinux.com. (
                        2001062502
                        21600
                        3600
                        604800
                        86400 )

      IN     NS     dns1.nwlinux.com.
      IN     NS     dns2.nwlinux.com.

      IN     MX     10     m1.nwlinux.com.
      IN     MX     20     m2.nwlinux.com.

             IN     A       10.1.10.25
server1      IN     A       10.1.10.25
server2      IN     A       10.1.10.25
olyubuntu    IN     A       10.1.10.26

```

---

### Post by SeijiSensei on 2010-12-08
From outside, olyubuntu.nwlinux.com resolves to 173.10.77.142.  Does that address forward to 10.1.10.26?

I see that nwlinux.com also resolves to this address, so I'm guessing that's the only external address you're using.  It sounds like you're expecting your router to somehow send inbound requests to the right internal host.  It's not equipped to do that.  In fact I think only an Apache reverse proxy behind the router can handle this.  Send all the requests to the .25 machine, but have a reverse proxy defined as the VirtualHost for olybuntu that forwards requests for that name to the .26 host.

---

### Post by R.Bucky on 2010-12-08
Right, I understand that olyubuntu.nwlinux.com resolves to that IP address. However, once a connection is made, my DNS should forward that VirtualHost to the correct machine based on my ANAME entry. It functions inside my network, but not externally. 

I do not expect my router to do NAT'ing - that is what BIND9 is for...

---

### Post by SeijiSensei on 2010-12-08
> **R.Bucky said:**
> Right, I understand that olyubuntu.nwlinux.com resolves to that IP address. However, once a connection is made, my DNS should forward that VirtualHost to the correct machine based on my ANAME entry. It functions inside my network, but not externally. 

I do not expect my router to do NAT'ing - that is what BIND9 is for...

A Google search confirms that there is no ANAME entry.  Searching for "bind ANAME" brings up only this thread.

There is a CNAME directive, but that just aliases one hostname to another. 

The reason it functions inside your network is that your internal nameserver has an A record for olyubuntu that points to the .26 machine.  External requests for port 80 are just going to arrive at your router's external interface and be forwarded to a single internal IP which appears to the .25 host.  DNS has nothing to do with any of this.

---

