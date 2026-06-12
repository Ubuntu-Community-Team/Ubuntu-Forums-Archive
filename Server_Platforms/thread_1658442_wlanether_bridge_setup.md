---
title: "wlan/ether bridge setup"
date: 2011-01-02
forum: Server Platforms
---

### Post by prolegomenes on 2011-01-02
Browsing here and there I finally succeeded (well almost) in setting  up my home-made router/firewall/filer/nameityougotit server. Everything seems to work (using ethernet or wireless connections) but I still have some questions:

WAN: eth0 
LAN: eth1 and wlan0 are bridged (br0) together

Question 1
I am unable to play games using UDP between wlan and eth1 although it works when both stations are connected to eth1. Any clue?

Question 2
I used ufw to help me setup IPTables but I am not really happy with this tools. Since my network configuration must be quite common, could anyone point me to a regular IPtable setup script or give me the rules I should add?

Tanks

---

### Post by prolegomenes on 2011-01-03
I autoreply to my question:
The solution to the filtering between eth1 and wlan0 (bridged together) can be found on the linux foundation bridge FAQ 
[http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge#No_traffic_gets_trough_.28except_ARP_and_STP.29](http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge#No_traffic_gets_trough_.28except_ARP_and_STP.29)

** *No traffic gets trough (except ARP and STP)***

 *Your kernel might have ethernet filtering (ebtables, bridge-nf,  arptables) enabled, and traffic gets filtered. The easiest way to  disable this is to go to /proc/sys/net/bridge. Check if the bridge-nf-*  entries in there are set to 1; in that case, set them to zero and try  again. *
 [I] # cd /proc/sys/net/bridge
 # ls
 bridge-nf-call-arptables  bridge-nf-call-iptables
 bridge-nf-call-ip6tables  bridge-nf-filter-vlan-tagged
 # for f in bridge-nf-*; do echo 0 > $f; done
[/I]

---

