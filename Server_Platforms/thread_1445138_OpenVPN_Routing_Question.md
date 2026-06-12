---
title: "OpenVPN Routing Question"
date: 2010-04-02
forum: Server Platforms
---

### Post by spynappels on 2010-04-02
Hi Guys,

I have an OpenVPN routing question I need some help with.

I have an OpenVPN server running, with 2 active daemons. It listens on port 1194 for the UDP service and  on port 1195 for the TCP service. Each service hands out addresses in a different subnet, 10.18.0.x for the UDP and 10.18.1.x for the TCP service, both with 255.255.255.0 subnet masks.

I want to allow traffic between the subnets so hosts on the TCP service and hosts on the UDP can talk to each other. I have pushed routes to the VPN Clients and I can ping 10.18.1.1 (VPN server address) from a 10.18.0.5 ip address, but when I try to ping or ssh into a different node on the other subnet such as 10.18.1.6, it simply times out or gets nor response.

Do I need to set up routes between the subnets on the VPN server? When I checked the routes, there were some there, I'm just not sure if they were the correct ones.

Any pointers or help would be appreciated, I can show routing tables from the server if I need to.

Thanks

---

### Post by jrssystemsnet on 2010-04-02
The OpenVPN server knows perfectly well how to get from one subnet to the other, it simply won't forward the traffic between them unless you tell it to.  You can either do this the traditional way, with iptables rules, or the simple-as-dirt way, simply by [enabling packet forwarding](http://ubuntuwiki.net/index.php/Packet_Forwarding).

Obviously, the iptables way gives you the ability to do other things like limit the types of traffic forwarded, but if you just want all traffic destined for one interface or the other to GET there, enabling IP forwarding is simple, fast, and effective.

---

### Post by spynappels on 2010-04-02
Doh, I had to do this on my other VPN server too.

Someday I'll remember stuff, thanks for the reminder.

---

