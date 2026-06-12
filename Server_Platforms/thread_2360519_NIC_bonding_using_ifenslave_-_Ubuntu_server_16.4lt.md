---
title: "NIC bonding using ifenslave - Ubuntu server 16.4lts - Configuration Issues"
date: 2017-05-05
forum: Server Platforms
---

### Post by marcouan on 2017-05-05
[FONT=arial][SIZE=2]Hello Guys, 
 
I'm trying to configure nic boding with ifenslave on Ubuntu server 16.4. 
I thought that this will be straight forward procedure but my configuration is not working. 
I tried several suggestions but all configuration suggestions fail. 

For starters I want to set up a simple active-backup bond interface with 2 slaves. 

bonding module is loaded. 

interfaces file: 

#eno3 configuration 
auto eno3 
iface eno3 inet manual 
bond-master bond0 
bond-primary eno3 
 
#eno5 configuration 
auto eno5 
iface eno5 inet manual 
bond-master bond0 
 
# Bonding eno3 &eno5 to create bond0 NIC 
auto bond0 
iface bond0 inet static 
address 192.168.5.200 
gateway 192.168.5.1 
netmask 255.255.255.0 
bond-mode active-backup 
bond-miimon 100 
bond-slaves none 
 
Bonding  interface comes up and is working only when eno3 is available. When we  bring down eno3 the bonding interface losses connectivity. 
 
Anyone with similar issues, advise. 
Thank you  
 
BR 
Antonis Marcou                                 [/SIZE][/FONT]

---

### Post by marcouan on 2017-05-16
Anybody has a working example on ubuntu srv 16.4LTS?
I found that when i unplug the cable the mii status shows up. 
Seems that the driver cannot detect the link failure.
anyone can help troubleshoot

---

### Post by marcouan on 2017-05-16
Hello 

Finally i found a solution. 
i changed the following directly in the ifenslave file.
fail_over_mac to active  --> MAC address of the bond should always be the MAC address of the currently active slave
and
use_carrier to 0 -->  Specifies whether or not miimon should use MII or ETHTOOL to determine the link status.

---

