---
title: "TAP interface not reporting speed"
date: 2014-11-06
forum: Virtualisation
---

### Post by GigabyteProduction on 2014-11-06
I created a VirtualBox virtual machine and configured a service to start it and shut it down with my system. I was networked with the machine with a host-only adapter, but have switched to bridging the virtual machine to a TAP interface due to VirtualBox's limited functionality when configuring interfaces on Linux, to prevent a problem with the MAC address of the host-only adapters, and to not interfere with hypothetical users of the computer who want to use virtual machines (I try to use best practices even if I'm the only one using the computer). It seems to work wonderfly, except that the TAP interface isn't reporting any proper speed or bandwidth statistics. I have the same statistics problem with the host-only interfaces, as well.

I created the interface with 'sudo tunctl -u servervm -g nogroup -t tap0' (tunctl coming from the uml-utilities package), so I think it may not be calculating bandwidth and showing the packets as lost because there's no program controlling the interface as there is when you use a TAP interface with a service such as OpenVPN. In fact, while testing, a TAP interface controlled by OpenVPN shows real statistics.

I have embedded below, and attached a screenshot that demonstrates the problem by sending enormous amounts of random data to the virtual machine with nc/netcat. The speed statistics in Conky (below "VPN"), ifconfig, and the Network Monitor panel item directly to the right of my notification and indicator area are nonexistent. I apologize for the low quality, the original file is actual size.
[ATTACH=CONFIG]257776[/ATTACH]
The computer is A0, the virtual machine is A4.

**What can I do to get the statistics to report properly (preferably while using a TAP interface)?**

---

### Post by GigabyteProduction on 2014-11-06
I have a mostly acceptable solution. I added the TAP interface to a bridge with bridge-utils, and the bridge interface is keeping track of traffic. The TAP interface can be in a bridge by itself. I'm really unsure if this is the proper solution. It makes me wonder if bridge interfaces don't take lost packets into consideration (since the original problem may have been caused by packets being considered lost). I guess it doesn't really matter if it doesn't look at lost packets. Since this is a virtual interface, I don't think packet loss really exists unless I make VirtualBox emulate packet loss. Either way, yay! (unless there's a better one)
[ATTACH=CONFIG]257793[/ATTACH]

---

