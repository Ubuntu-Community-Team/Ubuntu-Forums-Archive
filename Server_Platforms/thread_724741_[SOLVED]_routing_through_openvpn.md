---
title: "[SOLVED] routing through openvpn"
date: 2008-03-14
forum: Server Platforms
---

### Post by davidmaxwaterman on 2008-03-14
Hi,

I have set up an ubuntu server on my LAN and it has an OpenVPN tunnel to a remote network. I have set up squid on the server so web browsers can set their proxy to it and various addresses get routed through the OpenVPN tunnel - this is done by adding 'route' commands at the bottom of my OpenVPN client config file.

However, now I have more machines that need more than just web access to the networks at the other end of the OpenVPN tunnel, so I'd like to set the server up to route local LAN packets through the VPN tunnel.

My LAN's gateway to the internet is a Linksys WRT-54G running DD-WRT, and it has the facility to add routes to different networks, and I've added the remote LAN network to it, so that things get routed to my Ubuntu box.

However, it seems I still need to do something to the Ubuntu box in order for it to accept packets off the LAN and route them through the OpenVPN tunnel.

Can anyone enlighten me?

Do I have to install iptables to do NAT? It seems like it's overly complicated...if so, could someone explain why I can't just route from one network interface to another?

Thanks.

Max.

SOLVED: all I needed to do was 'echo 1 > /proc/sys/net/ipv4/ip_forward' and it worked - now all hosts on my network can get to the remote OpenVPN networks.

---

