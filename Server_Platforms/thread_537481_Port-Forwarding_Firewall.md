---
title: "Port-Forwarding Firewall"
date: 2007-08-28
forum: Server Platforms
---

### Post by leptogenesis on 2007-08-28
Hello,

I'm trying to set up a fairly informal server - not too concerned about security, but I'd like to do what I can for a cheap price.  I'm pretty new to security.

I want to be able to access my server through ssh (from anywhere, through some random port) and, more importantly, I want requests on port 80 to be forwarded to port 8080 where they'll be handled by my tomcat server.  I've gotten the iptables configuration from this website working (see the kernel space port forwarding section):

[http://www.klawitter.de/tomcat80.html](http://www.klawitter.de/tomcat80.html)

Naturally, I don't want any other traffic going through the firewall.  I've heard that most 'firewall' programs for linux are just front-ends for iptables...I think a firewall program will do a better job than I would at properly configuring iptables.  Unfortunately I can't find a firewall program that does port forwarding.  And I would think that most firewall programs (Shorewall, for example, seems to do that) would get rid of other iptables rules before loading its own rules.  

Does anyone know of a good way to do this kind of port forwarding while still keeping a cautious firewall configuration?

---

### Post by HermanAB on 2007-08-29
Some confusion here.

The Linux packet filter is called NetFilter.  NetFilter is a collection of Kernel Modules.  The front end to NetFilter is iptables.  Since iptables rules are a trifle arcane, there exists countless front-ends to iptables, of which Firestarter and Shorewall are probably the best known here.  Once these programs loaded the rules into NetFilter, they are done and typically terminate.  

Firestarter and others have options to monitor the system logs for results coming back from netFilter.  You can at any time monitor the system logs yourself from the command line using 'tail -f /var/log/messages'.

You can at any time augment the rule set by loading a new rule from the command line using iptables directly.  The best way to learn iptables, is to read the man page about ten times by when it should start to make a little sense, then trying your hand at a few rules.

Probably the best firewall script is Shorewall.  Shorewall can be managed via Webmin.

Hope that helps!

Cheers,

Herman

---

### Post by leptogenesis on 2007-09-01
Ok...so you think that there isn't a way for shorewall to coexist peacefully with the iptables port-forwarding scheme?  So I guess the idea is I should probably just learn iptables and not bother with shorewall?

---

### Post by HermanAB on 2007-09-02
Shorewall does certain things using iptables.  You can at any time add or remove rules using iptables yourself too.

To redirect one port to another, add this line to the end of /etc/rc.d/rc.local:
/sbin/iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080

Otherwise, you could just reconfigure Tomcat to listen on port 80.

Cheers,

Herman

---

