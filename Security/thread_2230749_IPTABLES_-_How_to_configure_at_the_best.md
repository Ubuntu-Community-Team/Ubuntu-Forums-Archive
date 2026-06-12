---
title: "IPTABLES - How to configure at the best?"
date: 2014-06-20
forum: Security
---

### Post by KaMZaTa on 2014-06-20
I've a server with an Hypervisor HN and some VMs.

This is more or less what I need:

_HN (87.x.x.56)_:

- SSH 22
- ping?
- apt-get working? I try to open port 53 for bind but doesn't work


_VM1 (192.168.1.10)_:

- apache


_VM2 (192.168.1.20)_:

- port 16000


_VM3 (192.168.1.30)_:

- port 20000


There are any basic rules good to set to prevent DDOS and others attacks? How can I configure at the best Iptables?

Can someone show me a very good example?

---

### Post by TheFu on 2014-06-21
Entire books have been written on this. I can recommend _Linux Firewalls_ by Rash as a starting point.
If you care about Linux security, start by reviewing the links in my signature.  Firewall rules are just the start, not hardly the total of security.

---

### Post by ubudog on 2014-06-21
The great bodhi.zazen has written a very helpful article on iptables, located [here]("http://bodhizazen.net/Tutorials/iptables").

---

### Post by KaMZaTa on 2014-06-22
Thank you both

---

### Post by HermanAB on 2014-06-25
Hmm, bear in mind that you cannot defend against a DDOS.  You would need the help of Akamai to keep a server under DDOS up and running.  Any DOS related rules are useless at the endpoint.

Most iptables rules promoted in papers and books are totally superfluous and based on bugs that were fixed a decade ago, the only purpose of which is to sell the book.  In practise a server on the WWW needs NOTHING.  No rules at all.  The Linux IP stack is fine.  It doesn't have bugs anymore.  It doesn't need any more rules.

That being said, I always install a general purpose rate limiting rule on a server, to discourage brute force password attacks.  That is all.

---

### Post by KaMZaTa on 2014-06-25
> **HermanAB said:**
> Hmm, bear in mind that you cannot defend against a DDOS.  You would need the help of Akamai to keep a server under DDOS up and running.  Any DOS related rules are useless at the endpoint.

Most iptables rules promoted in papers and books are totally superfluous and based on bugs that were fixed a decade ago, the only purpose of which is to sell the book.  In practise a server on the WWW needs NOTHING.  No rules at all.  The Linux IP stack is fine.  It doesn't have bugs anymore.  It doesn't need any more rules.

That being said, I always install a general purpose rate limiting rule on a server, to discourage brute force password attacks.  That is all.

These are just the basic rules that I used: limit rate and limit burst

---

### Post by cogset on 2014-06-26
On regard to this,I have lines like these in my iptables ```
avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 
```in reality I'm just using UFW to set my firewall,so I haven't really set up anything to specifically limit rate and limit burst:is this OK or should I go for something more restrictive?
Please keep in mind I'm talking about a normal desktop in my case.

---

### Post by FastZ on 2014-06-28
I keep a script that I use to build / update my IPTABLES on my Ubuntu server. Any time I need to open up a port or deny a certain port from receiving connections, I just update the appropriate section of the script and then run it in terminal. The script also adds two logging rules that log denied connections to syslog.

```
#! /bin/sh
#
# A simple firewall initialization script
#


# Flush any existing rules
iptables -F


# allow all connections for loopback int
iptables -A INPUT -i lo -j ACCEPT


# allow established sessions
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT


# allow incoming traffic on specific ports
iptables -A INPUT -p tcp --dport 22 -j ACCEPT        # incoming ssh
iptables -A INPUT -p tcp --dport 80 -j ACCEPT        # incoming http
iptables -A INPUT -p tcp --dport 10000 -j ACCEPT    # incoming webmin


# block all incoming traffic that does not meet any of the rules above this one
iptables -A INPUT -j DROP


# allow outgoing traffic on specific ports
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT        # outgoing dns
iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT        # outgoing smtp
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT        # outgoing http
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT        # outgoing https
iptables -A OUTPUT -p udp --dport 514 -j ACCEPT        # outgoing syslog


# block all outgoing traffic that does not meet any of the rules above this one
iptables -A OUTPUT -j DROP


# log dropped packets to syslog for review
iptables -I INPUT 6 -m limit --limit 5/min -j LOG --log-prefix "iptables denied IN: " --log-level 7
iptables -I OUTPUT 7 -m limit --limit 5/min -j LOG --log-prefix "iptables denied OUT: " --log-level 7


# save rules so they are persistent
iptables-save

```

---

### Post by HermanAB on 2014-06-29
Well, except for the limit rules at the bottom, that is a good example of a whole lot of rules that you don't really need on a modern system, since they won't really do anything different from what will happen by default.

---

