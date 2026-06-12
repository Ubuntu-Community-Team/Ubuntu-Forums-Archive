---
title: "Getting a well configured iptables setup"
date: 2009-07-07
forum: Server Platforms
---

### Post by Daimanta on 2009-07-07
Basically, I have to configure the firewall for a server I administrate but I am finding it difficult to properly configure the iptables setup because I do not really understand how iptables works.

I basically want to allow and deny access to my network and my server based on ip-groups.

How can I configure so that iptables discriminates based on ip and then follows routing protocols specifically meant for that particular chain? I want to configure it in such a manner that people from chain A can access a multitude of ports(like ssh,web,imap,smtp) , people from chain B are only allowed to access http and people in chain C basically get a free pass at trafic.

Also, I would like to know where the configfile of iptables is so I can save the filterrules by default.

---

### Post by slugmax on 2009-07-09
You want to create new chains with something like:

```

iptables -N webusers

```

Then selectively direct packets by source network into the new chains like this:

```

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -s 10.0.0.1/24 -j webusers
...
iptables -A webusers -p tcp --dport 80 -j ACCEPT
iptables -A webusers -p tcp --dport 443 -j ACCEPT
iptables -A webusers -j DROP

```

This drops all traffic for users in the chain 'webusers' that is not initiating a port 80 or 443 connection. Once the connection is established, it is allowed by the ESTABLISHED,RELATED line.

Remember INPUT is for connections to your server, OUTPUT is for connections from your server, and FORWARD is for connections *through* your server.

I have some scripts you might find useful as a starting point here:

[http://blog.unixlore.net/2006/03/linux-iptables-firewall-scripts.html](http://blog.unixlore.net/2006/03/linux-iptables-firewall-scripts.html)

---

