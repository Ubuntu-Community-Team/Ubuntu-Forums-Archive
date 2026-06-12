---
title: "OpenVPN connected but no DNS (Ubuntu 10.10 64-bit)"
date: 2012-12-03
forum: Security
---

### Post by hitchhiker2012 on 2012-12-03
Hi,

I followed this setup guide for OpenVPN on linode server: [http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid](http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid).

I've been able to connect successfully to the vpn network from a windows 7 laptop and can ping/access outside servers by IP addresses directly. However the browsers are not working which I suspect is due to DNS issue. 

Can anyone help with this? Let me know if there's more info I can provide that would help with the debugging.


Connection log from client side 
> Tue Dec 04 07:51:45 2012 [helios] Peer Connection Initiated with MYSERVER:1194
Tue Dec 04 07:51:48 2012 SENT CONTROL [helios]: 'PUSH_REQUEST' (status=1)
Tue Dec 04 07:51:48 2012 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 10.8.0.1,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5'
Tue Dec 04 07:51:48 2012 OPTIONS IMPORT: timers and/or timeouts modified
Tue Dec 04 07:51:48 2012 OPTIONS IMPORT: --ifconfig/up options modified
Tue Dec 04 07:51:48 2012 OPTIONS IMPORT: route options modified
Tue Dec 04 07:51:48 2012 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Tue Dec 04 07:51:48 2012 TAP-WIN32 device [Local Area Connection 2] opened: \\.\Global\{5330FAB0-6492-4995-8B1E-0BB8FD4A2436}.tap
Tue Dec 04 07:51:48 2012 TAP-Win32 Driver Version 9.9 
Tue Dec 04 07:51:48 2012 TAP-Win32 MTU=1500
Tue Dec 04 07:51:48 2012 Notified TAP-Win32 driver to set a DHCP IP/netmask of 10.8.0.6/255.255.255.252 on interface {5330FAB0-6492-4995-8B1E-0BB8FD4A2436} [DHCP-serv: 10.8.0.5, lease-time: 31536000]
Tue Dec 04 07:51:48 2012 Successful ARP Flush on interface [23] {5330FAB0-6492-4995-8B1E-0BB8FD4A2436}
Tue Dec 04 07:51:50 2012 TEST ROUTES: 2/2 succeeded len=1 ret=1 a=0 u/d=up
Tue Dec 04 07:51:50 2012 C:\WINDOWS\system32\route.exe ADD MYSERVER MASK 255.255.255.255 MYLAPTOP_IP
The route addition failed: The object already exists.
Tue Dec 04 07:51:50 2012 C:\WINDOWS\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 10.8.0.5
 OK!
Tue Dec 04 07:51:50 2012 C:\WINDOWS\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 10.8.0.5
 OK!
Tue Dec 04 07:51:50 2012 C:\WINDOWS\system32\route.exe ADD 10.8.0.1 MASK 255.255.255.255 10.8.0.5
 OK!
Tue Dec 04 07:51:50 2012 Initialization Sequence Completed
Tue Dec 04 07:52:15 2012 Replay-window backtrack occurred [2]


This is the iptables 
> Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  10.8.0.0/24          anywhere
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

---

