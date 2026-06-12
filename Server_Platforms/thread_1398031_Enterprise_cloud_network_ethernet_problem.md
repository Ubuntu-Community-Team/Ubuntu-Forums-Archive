---
title: "Enterprise cloud network ethernet problem"
date: 2010-02-04
forum: Server Platforms
---

### Post by MBetton@jasperss.com on 2010-02-04
Hey all good night. It has being a while me since the old Novell days, however I seem to be having some NIC problem, 
 
1. I have two servers, both has dual NICs (server1 CC) is configure (eth0 to ISP 97.xx.xx.xx), ( eth1 local 192.xx.xx.xx) goes to dhcp, On (server2 NC) eth0 local 192.xx.xx.xx goes to the dhcp. so this is the NIC setup
 
2. now with a clean cd installation there is no web access from (server1 CC) here is a look at my ifconfig
 
### Set up the local loopback interface
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 99.xx.xx.105
netmask 255.255.255.248
gateway 99.xx.xx.xx
 
auto eth1
iface eth1 inet dhcp
 
however if I change DHCP or Static to manual the web works great meaning, pinging, downloading updates etc. 
 
auto eth1
iface eth1 inet manual
 
oh yea with manual cannot ping between server1 and server2.
 
HELP PLEASE. 
 
there is bridging issues, would like the node to access the cluster without the use of nat.

---

