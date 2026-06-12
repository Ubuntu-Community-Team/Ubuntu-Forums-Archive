---
title: "OpenVPN Server and Router Settings"
date: 2017-11-09
forum: Server Platforms
---

### Post by databoy2k on 2017-11-09
Hey All:

This is so elementary it hurts to have to post, but for the life of me I can't figure this out. I couldn't get it on my own, and I've followed three separate tutorials now but suspect that it's a problem at my router.

Setup: Modem --> Wireless Router (running Shibby's Tomato) --> Clients. One such client is an Ubuntu Server (17.10). I'd like that server to administer the OpenVPN connection, so I've forwarded an external router port to the internal 1194 on the server.

I'm able to connect to the openvpn server from external clients (e.g. cell phone via cellular network), but once connected can't access the internet or the other clients under the Router. Obviously I'm missing something in routing, which is my absolute weakness.

Anybody with the patience of Job willing to lend a hand? I'm honestly not even sure what info you'll need right off the bat. 

Thanks.

--Edit: Paste per Advice: [http://paste.ubuntu.com/25926903](http://paste.ubuntu.com/25926903) --

---

### Post by wildmanne39 on 2017-11-09
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by databoy2k on 2017-11-09
Thanks.

[http://paste.ubuntu.com/25926903](http://paste.ubuntu.com/25926903)

---

### Post by darkod on 2017-11-09
OpenVPN client by default can connect only to the OpenVPN server. So, it is working as expected.

To make your ubuntu server route traffic for vpn clients you need two things (assuming you are not blocking any traffic with iptables or another firewall):
1. Open /etc/sysctl.conf and enable (uncomment) the line 'net.ipv4.ip_forward=1'. That allows IPv4 forwarding. Reboot the server to make it effective.
2. Create iptables rule for MASQUERADE (NAT). That is needed for traffic to be able to be routed correctly:
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

That rule is not permanent, it gets lost on reboot. If you don't have other iptables rules that are applied, the easiest way to apply it on each boot is to put it in /etc/rc.local (before the exit 0 line). The command will be executed at the end of each boot. NOTE: You don't need the sudo when putting commands in rc.local, they are executed as root anyway. So don't put sudo in there.

The above two steps should get your clients working.

---

### Post by databoy2k on 2017-11-09
I've confirmed both that forwarding is enabled and that the iptables are set up. Thanks for confirming that for me. 

I must have some router-setting issue. Any tips on what I might need to work with? Again, this is Shibby's Tomato firmware running on it.

---

### Post by darkod on 2017-11-09
Hmmm, your router shouldn't have anything to do with this...

1. The ubuntu server can access the internet correctly, right?
2. The clients can connect to the openvpn, right?

If both answers are YES, then it should work. After the client connects to the openvpn the traffic is routed as if the ubuntu server itself is sending it...

Also, before setting this up did you plan what you actually want to achieve? Because many people might follow a tutorial without really understanding that something else might work better for them.

Best example is whether you want all client traffic to be routed over the vpn or only specific traffic destined for the openvpn server and some LAN clients? The answer to this question makes big difference in how you need to set up the openvpn server conf file.

---

### Post by databoy2k on 2017-11-09
Hey:

Hm. Both were true to begin with, but since rebooting the server I don't have DNS on the server. I can ping, e.g. 8.8.8.8, but not "google.com".

I'm almost at the point of starting fresh on this server; clearly I've messed something up. Think that's the best option, or where should I go now?

The goal is for the clients to direct all traffic through the server and access all clients connected to the network. The server itself is just a client of the network. My goal is to have the vpn clients effectively function as additional members of the network, to be seen and see all, just via the secure vpn tunnel. It's a home network.

---

### Post by darkod on 2017-11-09
The server is standard installation, you didn't add any GUI to it?

If you are working in CLI, then the networking options are in /etc/network/interfaces. You should check there which DNS servers you set up with dns-nameservers. You can post the file content if you are unsure what is what...

And the server should have static IP, especially since you are forwarding external port to it.

---

### Post by databoy2k on 2017-11-10
I've cheated somewhat; I've assigned static IPs via Tomato on the router. 

I attempted to flush the IP and lost SSH communication with the server. Clearly I had some more significant problems than I thought.

Are you able to point me towards an OpenVPN config that would do effectively what I'm looking for? I'm going to get the networking in order before I continue trying to get the VPN running.

---

### Post by databoy2k on 2017-11-12
For anybody who stumbles onto this question, no, my router in my case didn't need any static routing. To answer my last question, I followed Digital Ocean's tutorial [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04) but allowed the cipher to stay at the default AES-256-CBC (I assume the tutorial is old). This time it worked. Obviously I borked something badly last time.

Thanks for your patience @darkod.

---

