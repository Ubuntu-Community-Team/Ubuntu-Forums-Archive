---
title: "iptables port forwarding"
date: 2009-03-09
forum: Server Platforms
---

### Post by Carello on 2009-03-09
Hello,

first off, let me start with saying that I've tried searching the forums and googled the topic extensively, to no prevail.

If there's anyone familiar with iptables and routing who can help me, I'd greatly appreciate it.

Okay, so let's get going...

The layout of my network is basically this:

Internet->Router(Windows server running several services)->Ubuntu server and clients

The local network is using a C class IP range (192.168.10.0/24) and the OpenVPN server is handing out IP addresses in an A class range to VPN clients (10.8.0.0/21).

The Ubuntu server is set up as an OpenVPN server (running as a virtual machine on the Windows server), and the main router is forwarding traffic on UDP port 1194 to the Ubuntu server.
On the Ubuntu server, I need to forward traffic on certain ports, from the VPN connections, back to the main router. The OpenVPN server is supposed to only be used for VPN clients to access certain services on the main router, and to block access to the rest of the network.

So, I figured the easiest way would be to set up the OpenVPN server, configure iptables to forward traffic on port x back to the router from where the traffic came from, but it turns out I could not make it work. I've tried lots of different solutions found while searching, including several different command line tools and GUI's to aid with iptables configuration(fwbuilder, bastille etc.), but nothing I've done has been able to forward traffic over the VPN tunnel back to the router...

Is there anyone out there who can think of a solution for this?
My iptables and routing knowledge unfortunatly seems to be lacking as I can't make this work on my own.

Please, I desperatly need help to get this working...thank you.

---

### Post by cdenley on 2009-03-09
Have you tried DNAT?
[http://linux-ip.net/html/nat-dnat.html](http://linux-ip.net/html/nat-dnat.html)

---

### Post by Carello on 2009-03-09
Thank you for the reply, cdenley.

Yes, I have tried DNAT but have not been able to make it work...

What's weird though, is that I have set the log level to debug for the PREROUTING chain where the DNAT rules are located, without the DNAT rule to forward packets, it logs everything, with it enabled, nothing is logged.

Could it be because the packets are being forwarded or because something is wrong? I figured the debug level should log everything, including forwarded packets...

---

### Post by BoGs on 2009-04-14
On my vpn i have forwarding using SNAT all 10.8.0.0/24 to my public ip address as I use it to go to HULU and Pandora.

the command is 

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j SNAT --to <ip address>

---

