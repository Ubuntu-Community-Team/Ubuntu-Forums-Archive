---
title: "Ubuntu DNS server recursion and iteration"
date: 2013-06-25
forum: Server Platforms
---

### Post by MadsRC on 2013-06-25
I've started reading the book "DNS and BIND 5th Edition" and I'm about half way through it.

I couldn't really wait, so I fired up a virtual machine on a DMZ network on my ESXi server to do some testing. Sofar I've gotten a Ubuntu 12.04.2 server up and running OpenSSH and BIND (From the repo, version 9.something)

While I got most things covered sofar, there is one particular thing I can't really figure out.
For security reasons, you should disable recursive resolving or atleast limit it. I went for the disable solution, as I wante to test iterative querying.

I've been told, and I've read that disabling recursion (With the "recursion no" option) will enable itertion.
Which I think is working, because a "dig @ip.of.dns.server google.com" resolves into google's IP (or recursion really is still enabled, can't see that from dig".

This led me to believe I could use the DNS server (Hypothetically, I know it's not good practice) as both an authorative nameserver (For my own domain) and as a DNS server for my DHCP/network clients.

Problem is that the Windows resolver won't resolve ANY URL using my nameserver (With recursion disabled... with it enabled, it works fine.) same goes for Windows NSlookup.

Tried it with a Ubuntu machne, same result. Ubuntu's nslookup won't resolve either, but dig can...

Am I doing something wrong, or is it normal for resolvers not to be able to cope with the nameservers "I don't know, but you could try asking XXX.XXX.XXX.XXX" message it returns when recursion is disabled?

PS: I know the correct and best way would be to have 2 nameservers. One (or more) as authorative nameservers, and one (or more) for client lookups.

---

### Post by SeijiSensei on 2013-06-25
Is the server's Ethernet address in the listen-on {} list in named.conf?  Maybe it is only listening on localhost so the other machines on the network cannot see it?

```

options {
     directory "/var/named";
     listen-on { 127.0.0.1; 10.10.10.10; };
     
     [stuff]

};

```

---

### Post by MadsRC on 2013-06-26
It is listening on all interfaces.

Maybe I wasn't perfectly clear.

If i disable recursion, my clients (Standard windows and ubuntu 12.04) can't resolve domains.
If I enable recursion, they can resolve domains perfectly fine.

The only difference there is in my named.conf.options is that, when recusion is disabled, it has the following line: recursion no
When it's enabled, that line is commented out or removed.

---

### Post by SeijiSensei on 2013-06-26
Do you have a "query-source" option?  If so, does it use the Internet-facing interface?  What port does it use?

Can you post your named.conf?  You can leave off any zone declarations.  It the options{} section that it would help to see.

---

### Post by Doug S on 2013-06-26
Isn't the issue here that recursion does need to be enabled for the internal clients? But if your DNS is also externally facing, you would want recursion disabled for that? 
My DNS server doesn't work for my local clients either, if I disable recursion. DNS on my LAN is for local use only, so I block incoming requests for port 53 in my iptables rule set. However, if mine was externally facing, I would have this line in my named.conf.options file (using an example internal sub-net (the same as Seiji used)):```
allow-recursion { 127.0.0.1; 10.10.10.0/24; };
```As it is, and because of my iptables rule, mine is like this:```
        recursion yes;
        allow-recursion {any;};
```

---

### Post by SeijiSensei on 2013-06-27
If you block incoming port 53 traffic, then your server cannot communicate with the roots and resolve names outside the domains for which it is authoritative.

---

### Post by Doug S on 2013-06-27
> **SeijiSensei said:**
> If you block incoming port 53 traffic, then your server cannot communicate with the roots and resolve names outside the domains for which it is authoritative.To clarify, I don't specifically block incoming for destination port 53, but it since it isn't specifically allowed, it gets blocked. Requests from my DNS that go upstream, do so via another, high numbered, port and get back via the RELATED,ESTABLISHED path through my iptables. Some examples: First, a random incoming DNS request (entire session, packet was DROPPED):```
2013-05-07 10:36:15.229465 IP 180.76.5.159.63468 > XXX.XXX.XXX.XXX.53: 17924+ A? www.google.com. (32)
```Second, a forward request to a root server (F):```
2013-05-07 11:25:49.605652 IP 173.180.45.4.6485 > 192.5.5.241.53: 13848 [1au] A? bit.ly. (35)
2013-05-07 11:25:49.605829 IP XXX.XXX.XXX.XXX.14304 > 192.5.5.241.53: 8338 [1au] NS? . (28)
2013-05-07 11:25:49.781905 IP 192.5.5.241.53 > XXX.XXX.XXX.XXX.14304: 8338*- 14/0/23 NS i.root-servers.net., NS c.root-servers.net., NS g.root-servers.net., NS h.root-servers.net., NS b.root-servers.net., NS m.root-servers.net., NS j.root-servers.net., NS l.root-servers.net., NS e.root-servers.net., NS f.root-servers.net., NS d.root-servers.net., NS a.root-servers.net., NS k.root-servers.net., RRSIG (857)
2013-05-07 11:25:49.787509 IP 192.5.5.241.53 > XXX.XXX.XXX.XXX.6485: 13848- 0/8/10 (568)
```There is never a packet leaving my network from port 53.

---

### Post by MadsRC on 2013-06-27
Doug S, I guess your right.

I'm well aware that I could just limit recursion to my localnet.
That is the way I intend to do it on a live system.

I just thought I read that it would still work without recursion, but I guess I'm wrong.

Thanks for the input guys :D

---

