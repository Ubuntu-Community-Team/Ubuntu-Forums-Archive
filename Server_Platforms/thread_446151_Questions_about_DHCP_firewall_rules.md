---
title: "Questions about DHCP firewall rules"
date: 2007-05-16
forum: Server Platforms
---

### Post by nick1 on 2007-05-16
Greetings,

I am in the process of learning Netfilter/IPtables.  I plan on using Netfilter/IPtables to protect my Linux
desktop computers and servers.  We're talking host-based firewalls, not one firewall protecting all
of the desktops and servers.

I have a basic question I am hoping someone on this mailing list can answer.  I am a little confused about
configuring Netfilter/IPtables on a Linux desktop computer.  Specifically, this situation:

a linux desktop computer that is configured to use DHCP and configured to use the following rule:

```
$IPTABLES -A INPUT -s $IP_LOCAL -j LOG --log-prefix "Spoofed source IP"
$IPTABLES -A INPUT -s $IP_LOCAL -j DROP
```

I would like to include the previous rule as part of a standard rule set.

From how I understand this situation, the firewall would have to be able to automatically detect when the
computers IP address changes, right?  Manually inputting the computers IP address each time it changes would get really old.

I'm using several books as references for learning Netfilter/IPtables and they discuss implementing "dynamic firewall scripts".  In this case, a dynamic firewall script that recognizes when the computers IP address changes.

So, my questions are:

1.) If I am using a computer that is configured to obtain its IP address through DHCP, what firewall rules do I need to setup?

2.) Additionally, how do I configure the firewall to automatically detect changes in the computers network
configuration (IP address change, etc.)?

Thank you for your time,

---

### Post by turinglabs on 2007-05-23
> **nick1 said:**
> Greetings,
```
$IPTABLES -A INPUT -s $IP_LOCAL -j LOG --log-prefix "Spoofed source IP"
$IPTABLES -A INPUT -s $IP_LOCAL -j DROP
```
...

So, my questions are:

1.) If I am using a computer that is configured to obtain its IP address through DHCP, what firewall rules do I need to setup?

2.) Additionally, how do I configure the firewall to automatically detect changes in the computers network
configuration (IP address change, etc.)?


Anti-spoofing should always be done with respect to a particular interface (with INPUT you would have to add '-i eth0', for example), the rule above could apply to your loopback (lo) interface as well, dropping unintended traffic. You may have a rule prior to that that allows all loopback traffic (most iptables scripts do), so you might not see that problem. 

The Linux kernel already has a way to do this, with reverse path filtering. You can turn it on with 'sysctl -w net.ipv4.conf.all.rp_filter=1' (or per-interface with sysctl -w . net.ipv4.conf.eth0.rp_filter=1'. You can also set it to '2' for full filtering, using 1 just filters on directly attached subnets. See [http://www.linuxguruz.com/iptables/howto/2.4routing-13.html](http://www.linuxguruz.com/iptables/howto/2.4routing-13.html) for an old, but still valid explantion. 

One final thing - for a desktop system, this probably isn't  necessary, since packets are always going out the same interface they come in. It is really only useful on routers or routing firewalls where you might have a spoofed reply packet go out an interface it is not authorized to.

I have two scripts you can take a look at [http://geekpit.blogspot.com/2006/03/linux-iptables-firewall-scripts.html](http://geekpit.blogspot.com/2006/03/linux-iptables-firewall-scripts.html) that might be useful.

HTH,

Doug

---

