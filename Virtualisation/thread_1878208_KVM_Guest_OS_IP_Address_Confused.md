---
title: "KVM Guest OS IP Address Confused??"
date: 2011-11-09
forum: Virtualisation
---

### Post by Dale Marthaller on 2011-11-09
I'm running Ubuntu 11.10 server as the Host OS. I have network bridging configured. I have migrated a physical Ubuntu 10.04 machine as a Guest OS on the server mentioned above. The Physical IP of the host is 192.168.10.112.
 
My question is related to the IP address of the Guest OS. In the guest I have a /etc/network/interfaces configured setting the IP as a static IP 192.168.10.100 but according to ifconfig this Guest is assigned 192.168.10.115 (This is in the DHCP range administered on the LAN router).
 
So why does this machine ignore it's settings in the /etc/network/interfaces and instead use a DHCP IP?

---

