---
title: "iptables port connection limit rule"
date: 2008-10-05
forum: Security
---

### Post by Shwick2 on 2008-10-05
I'm trying to secure my ssh port with iptables.  So far I successfully limit one ip to connect once a minute:

iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 -j DROP

How would I add a rule that limits the total number of connections to 10, on port 22?

---

### Post by kevdog on 2008-10-05
Just to clarify -- you mean like 10 clients connecting at one time to the server?

---

### Post by Shwick2 on 2008-10-06
To clarify, I want two rules:

1) A connection to port 22 can only be made once every 60 seconds per IP.
Edit* 2) There can only be 10 new connections to port 22 every 5 minutes, regardless of IP.

The original two iptables lines I listed enforce rule 1), look here for reference: [http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187).

I'm trying to build rule 2).  I don't want rule 2) to be based on IP, I just want to allow 10 connections from any number of IPs at once to port 22.

---

### Post by Shwick2 on 2008-10-07
I looked around and people were saying the --limit and --limit-burst would limit concurrent connections, no matter the IP.  I only have two comps so I haven't tested it out on multiple machines yet- it works against one.

iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 -j DROP
iptables -A INPUT -p tcp --dport 22 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

I would rather have the --limit rule first, but I haven't found a way for it to say, "continue to the next rule if true, drop if false".  Then if someone does a DDOS attack with a big botnet the packets will get dropped before going through two rules.

Ideally:

iptables -A INPUT -p tcp --dport 22 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j "continue to the next rule if true, drop if false"
iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 -j DROP
iptables -A INPUT -p tcp --dport 22 -i eth1 -m state --state NEW -j ACCEPT

---

### Post by cariboo on 2008-10-07
Just as a point of interest, you can open as many ssh connections as you've got terminals, from one computer.

Jim

---

