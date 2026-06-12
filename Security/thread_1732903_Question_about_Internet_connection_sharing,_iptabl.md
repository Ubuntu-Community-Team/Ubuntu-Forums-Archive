---
title: "Question about Internet connection sharing, iptables, and ufw."
date: 2011-04-18
forum: Security
---

### Post by Jive Turkey on 2011-04-18
My home network accesses the net through a headless ubuntu server like so:

Internet<--->server box<--->router<---<multiple computers

I set up the sharing/forwarding/NAT with three iptables rules:

```
## iptables rules for ICS
iptables -A FORWARD -o eth1 -i eth0 -s 10.10.10.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

Even though I have attempted to configure my LAN's services to only listen/serve to eth0 and my 10.10.10.0 subnet some insist (i.e. dnsmasq) on listening on the outward facing interface (eth1).

I would like to add some more firewall rules to shore this up without breaking the ICS, so my questions are these:

Will fw rules created with ufw interfere with the above ICS rules (they are applied via script called from a "post-up ICSrules.sh" in /etc/network/interfaces)?

I'm at kind of a loss as to how to craft some useful rules for this, TIA for any suggestions.

---

### Post by Jive Turkey on 2011-04-19
Some expirimentation has revealed that yes, ufw will most certainly bork things up for me.  It looks like I will need to dig in to some documentation on iptables.

---

### Post by uRock on 2011-04-19
I haven't used it yet, but Shorewall in Synaptic looks like it may be useful.

---

### Post by Jive Turkey on 2011-04-19
It looks like shorewall is just another front end to iptables, I'm checking it out now. I'm still undecided as to weather it is actually simpler to use or not.  There seem to be a lot of documented use cases similar to mine which is encouraging.

---

### Post by bodhi.zazen on 2011-04-19
IMO iptables is the way to go =)

It takes a little time to understand the syntax, but you are well on your way.

---

### Post by Jive Turkey on 2011-04-20
Well I have it working quite well with shorewall and my ICS has survived the reboot of server and clients. All my stuff appears to work except mysteriously, for X11 forwarding.  

A pure iptables implementation still seems more sexy from a small footprint of running code point of view.  I might just look into exporting my shorewall generated iptables rules and applying them directly once I know that I'm done tweaking things.  

This box has been running 24/7 for months with no firewall, connected directly to the net.  I wasn't all that concerned about security before but I'm happy to know I made a small gain in that area today.

Some links I found really helpful (shorewall has some of the best FOSS documentation I have seen to date):
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)
[http://open-ravi.blogspot.com/2006/09/setup-shorewall-with-two-interfaces.html](http://open-ravi.blogspot.com/2006/09/setup-shorewall-with-two-interfaces.html)
[http://www.wowtutorial.org/tutorial/16.html](http://www.wowtutorial.org/tutorial/16.html)

---

### Post by bodhi.zazen on 2011-04-20
[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

---

### Post by Jive Turkey on 2011-04-20
> **bodhi.zazen said:**
> [http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

That's about what I had before the shorewall adventure, except I was using dnsmasq instead of dhcp3-server and bind9.  While it worked just fine I wanted some more lock-down from the firewall to prevent my services from leaking out on the net.  

I was at a loss about how to craft iptables rules for locking down one interface without breaking the NAT for ICS.

---

### Post by Jive Turkey on 2011-04-22
I got the X11 forwarding fixed, I think shorewall may have changed something with the lo interface.

I tried lots of edits to sshd_conf and I think the line that fixed it was:
```
X11UseLocalHost yes
```
Forwarded windows no longer display "on $HOSTNAME" but that's no big deal.

---

