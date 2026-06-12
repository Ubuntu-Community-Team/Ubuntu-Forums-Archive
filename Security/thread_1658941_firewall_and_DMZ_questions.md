---
title: "firewall and DMZ questions"
date: 2011-01-03
forum: Security
---

### Post by methodtwo on 2011-01-03
Hi there
I'm currently wanting to set up a network with 2 Ubuntu servers(mail and web) in a DMZ in order to separate them from an internal network. I want to use a dedicated Linux firewall. This firewall will have 3 network interfaces on it. One network interface will connect to the external router/modem(router and modem in one box), one interface will connect to the DMZ and the other interface will connect to the internal network. The router/modem lets you put, i think it's 1 or 2, interfaces in a DMZ. But, when i think of any of the dedicated firewall's or servers' interfaces it doesn't make sense to me to put any of them in the router/modem's DMZ( I'm think it would be better for the dedicated firewall's and the servers' interfaces to have static private I.Ps ie 192.168.2.4 etc right?). What i mean is that even if, as far as the router/modem is concerned, none of the interfaces were in a DMZ, the area where the servers are would still effectively be a perimeter network and with such a set up would still be, effectively,a DMZ, right?. If i should put any of these interfaces in this DMZ please let me know which one.
Thank you for your time. This is really not a joke i am in fact still a UINX n00b
regards

---

### Post by methodtwo on 2011-01-03
I think i'm just going to put the external interface of the dedicated firewall in the DMZ of the external router/modem. Then i can put the servers in the DMZ of the dedicated firewall. Then i can have the dedicated firewall performing NAT and DHCP for the servers in the firewall's DMZ and the hosts on the internal network. Thank you for your time
regards

---

