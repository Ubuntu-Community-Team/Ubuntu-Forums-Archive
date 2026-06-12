---
title: "Changing outbound NAT IP"
date: 2014-05-16
forum: Virtualisation
---

### Post by logandzwon on 2014-05-16
Hey guys,
  For various reasons I need to set something for work in a specific yet none conventional way.

Basically, my box has an IP and that IP has an IP range routed to it. The VM is running with NATed access to the internet. The needed ports are fwded to the VM. All of that is working fine.

However, the server is sourcing outbound connections from the primary IP. Not the IP NATed to it. (Since it is "closest" to the internet and that is default behavior.)

I need to override that default behavior to originate the connections from one of the IPs in the range.

I've add an ip route;
/sbin/ip route change default dev em1 src 8.8.80.109

When I originate a connection from the host hypervisor it will originate from the desired IP. However the NATing seems to happen prerouting, so it is not using the desired source IP.

Is there a way to get the system to NAT this VM via em1:0 addr:8.8.80.109 instead of the default?


em1      inet addr:8.8.116.251  Bcast:8.8.116.255  Mask:255.255.255.0


em1:0   inet addr:8.8.80.109  Bcast:8.8.80.109  Mask:255.255.255.255

---

### Post by TheFu on 2014-05-16
Read everything carefully and I don't understand what you want.  Could you please specify
* the subnet.IP on the hostOS
* the desired subnet/IP for the guestOS
* whether DHCP is used  - and where
* which hypervisor and 
* which bridging/NAT it is using

A network diagram would really help too.

Oh - and how many NICs you can use.

---

