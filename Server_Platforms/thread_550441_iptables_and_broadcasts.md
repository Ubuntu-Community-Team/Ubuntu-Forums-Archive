---
title: "iptables and broadcasts"
date: 2007-09-13
forum: Server Platforms
---

### Post by Simba87 on 2007-09-13
Hi!
I registerd here because I thought that this forum seems rather busy and chances are that someone can answer my question.

I'm running a server with multiple network interfaces but it's not possible to broadcast between them.
The most important interfaces are eth0 (connected to a network with 192.168.1* IPs) and the pptp server (because of a proxy arp problem I have to use 192.168.1.* IPs here, too)
My iptables rules for the pptd server look like this at the moment:
```
iptables        -A forwarding_rule -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
iptables        -A output_rule     -o ppp+ -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
iptables        -A input_rule      -i ppp+ -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
```
Works pretty flawlessly, except for broadcasts. Is it impossible to do that without bcrelay? I thought it must be possible because the pptp clients are handled as seperate interfaces, right?
Another similar problem is that another virtual interface (VLAN) uses 192.168.0.* IPs and broadcasts between the 1.* and 0.* are not possible.
I would be soo grateful if someone could give me a hint on how to solve this with iptables. And I'm sorry for my bad English :(

---

### Post by a9k on 2007-09-14
I'm not sure what you are trying to do. If you mean broadcasting of arp packets to make a kind of bridge - [http://lartc.org/howto/lartc.bridging.proxy-arp.html](http://lartc.org/howto/lartc.bridging.proxy-arp.html)
pptp is 1<->1 Maybe you want a VPN?
[http://en.wikipedia.org/wiki/Virtual_private_network](http://en.wikipedia.org/wiki/Virtual_private_network)
Maybe you want a bridge? 
[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)

---

### Post by Simba87 on 2007-09-14
Thanks a lot for your answer, I really appreciate your try to help me :)

The PPTPd server I mentioned above is for creating VPNs. Proxyarp is enabled in it's configuration file. Normal network communication works flawlessly (from PPTP clients to local clients and vice versa) - but broadcasts are a problem (broadcasts like sending ICMP packets with 'ping -b 192.168.1.255' or in Windows with 'ping 192.168.1.255')).
The server gets those ICMP packets (checked that with tcpdump) but it doesn't route them to the clients of the local network. So, my question is how I could forward those broadcast to all clients of the local physcial network.

If only I'd have the ability to describe that better... :(
```

VPN client (PPTP, WinXP) ----> Server (Linux)                ----> Local Clients
ping 192.168.1.255       ----> tcpdump: ICMP packets arrived ----> tcpdump: no ICMP packets
```

but the local clients should get those ICMP packets, too.

I want to forward the arriving broadcasts frome one interface to another with iptables. Is that possible or does all this make no sense? (but there definitely must be a way to get the broadcasts through the VPN to the physical LAN, I just don't know how)
I'm growing desperate, already.

---

