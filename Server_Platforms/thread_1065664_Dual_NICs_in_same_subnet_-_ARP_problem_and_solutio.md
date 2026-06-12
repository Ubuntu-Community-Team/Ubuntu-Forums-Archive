---
title: "Dual NICs in same subnet - ARP problem and solution"
date: 2009-02-10
forum: Server Platforms
---

### Post by rempler on 2009-02-10
Hello everybody,

i want to thank the user **wideLoad** here and point out his solution for other users who maybe suffer the same problem: connecting two NICs on one machine to the same subnet and receiving ARP mixups. In my case, i wasn't able to setup two ports of a network card simultaneous. Every time the second ethernet device got a fixed IP address (in the same subnet) both IPs couldn't be reached any more from outside the router. I was able to source the error down to the ARP requests send from the last online brought NIC. The second NIC always produced a ARP mixup in the router tables. Luckily i found this thread under the forum archive [**http://ubuntuforums.org/showthread.php?t=566908**]("http://ubuntuforums.org/showthread.php?t=566908") and it really saved my day...
I know it's kind of a "bad thing" to use two NICs on one machine within the same subnet but i think this configuration best fits my needs of one single server (Ubuntu v8.10 64bit server) hosting several virtual machines via KVM:
... <-> router <-> eth0 <-> fileserver
... <-> router <-> eth1 <-> firewall <-> mailserver
... <-> router <-> eth1 <-> firewall <-> webserver
... <-> router <-> eth1 <-> firewall <-> forumserver

So for those of you thinking maybe of the same setup here's what i did for a permanent network configuration (/etc/network/interfaces):

# ===
auto eth0
iface eth0 inet manual
# ---
auto br0
iface br0 inet static
post-up /sbin/ip rule add from xxx.xxx.167.1 lookup 10
post-up /sbin/ip route add table 10 default via xxx.xxx.167.254 src xxx.xxx.167.1 dev br0
address xxx.xxx.167.1
netmask 255.255.255.0
network xxx.xxx.167.0
broadcast xxx.xxx.167.255
gateway xxx.xxx.167.254
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers xxx.xxx.xxx.xxx
dns-search xxx
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
# ===
auto eth1
iface eth1 inet manual
# ---
auto br1
iface br1 inet static
post-up /sbin/ip rule add from xxx.xxx.167.2 lookup 11
post-up /sbin/ip route add table 11 default via xxx.xxx.167.254 src xxx.xxx.167.2 dev br1
address xxx.xxx.167.2
netmask 255.255.255.0
network xxx.xxx.167.0
broadcast xxx.xxx.167.255
gateway xxx.xxx.167.254
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers xxx.xxx.xxx.xxx
dns-search xxxx
bridge_ports eth1
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

Also add this line in /etc/sysctl.conf:
net.ipv4.conf.all.arp_filter=1

I'm not sure if there are any other sources i could have consulted before running into this problem but the google search "ubuntu server two nics same subnet" found me wideLoads thread. Hope this here helps others from wasting a lot of time (like i did ;).

Thank you Ubuntu community
rempler

---

### Post by windependence on 2009-02-10
OK if you could explain exactly what this does, it would be great as I have the same problem on a BSD box running in VMware. I created another virtual switch but since the external cards are connected to the same network anyway, I still get the ARP messages. The connection works in FreeBSD, and people say it should be just fine, but if ai am getting errors, I want them fixed, and the site is very slow, and I can't figure out why. I suspect this is my problem. 

At any rate, I need to know what is going on here, and most of my networking and firewalling is done in BSD which is much different than Linux.

-Tim

---

### Post by rempler on 2009-02-10
Hi Tim,

i don't think i can "exactly" explain the underlying problem - i'm sure there are others out there who can ;) - but as far as i understand the problem is related to ARP sendings from the NIC to the router.
As soon as i assigned a fixed address (same subnet) for the second NIC the router tables showed double entries:

* single NIC on
1st MAC/NIC <-> IP assigned
* both NICs on
1st MAC/NIC <-> IP assignment deleted
2nd MAC/NIC <-> both IPs assigned (from the router side: stealing IP from 1st NIC)

"That's why" the ARP-Filtering must be enabled and the routing tables must be fixed!? Maybe wideLoad (or other users here) can explain it more correctly (or explain it at least)...

---

