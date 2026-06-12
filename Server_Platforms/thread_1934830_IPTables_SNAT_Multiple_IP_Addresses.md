---
title: "IPTables SNAT Multiple IP Addresses"
date: 2012-03-02
forum: Server Platforms
---

### Post by Frizianz on 2012-03-02
Hey guys,

I've got a /29 subnet from my ISP. Got a Linux box running as a GW server to do my NAT and VLAN's back to my switch. Basically wanting to NAT to different IP addresses based on source vlan.

What is the best way to do this? I haven't managed to get this working.

Cheers

---

### Post by nsnidanko on 2012-03-06
I am not very familiar with advanced outbound NATing with Linux. What I can suggest, if your GW box only does function of the router i would look into pfSense.

You can do inter-VLAN routing using router on the stick model:

Here's an example:
[http://blog.stefcho.eu/?p=695](http://blog.stefcho.eu/?p=695)

Outbound NAT can be configured using webGUI in a few simple clicks as well.

---

### Post by Frizianz on 2012-03-07
Rather not use a GUI, it does my VPN termination as well as my VPN connection to work.

Also other reason for keeping it how it is. I'm running it on a HP DL320 G2 which drivers for controlling the fan speeds are hard to get on non debian or RH operating systems. 
Gotta have the drivers or its like death to my ears.

If anyone knows how to do this via CLI that would be spendid.

Fraser

---

### Post by koenn on 2012-03-09
assuming vlans have each their own subnet, have you tried simply making masq or snat rules with '-s' parameter, something like 
' iptables -s subnet/mask   -j SNAT --to-source ... '
?

---

