---
title: "Using my system as a LAN host"
date: 2007-10-20
forum: Server Platforms
---

### Post by Dr Small on 2007-10-20
Hello,
I have the firestarter firewall installed, and I want another computer to connect to me as the host, to be able to access the network and internet.

My computer receives internet and network from the router, but I want to try this. I want the other computer to connect to my network IP address, and route everything through my firewall and then through the router to the internet.

Currently, LAN works.
I setup firestarter to "Enable internet connection sharing", went to the other pc, setup a static IP address, entered the host as the computer's network IP with firestarter, subnet as default (255.255.255.0) and LAN works. But I can not connect to the internet from the other pc.

Any idea how to do this?
By the way, I am only experimenting :D

Thanks!
Dr Small

---

### Post by HermanAB on 2007-10-20
Plug in a second ethernet adaptor and then then do soemthing like this:
# Bring the ethernet ports up
ifconfig eth0 142.59.19.115 netmask 255.255.254.0 hw ether 0:13:46:fa:c8:d2 up
ifconfig eth1 192.168.1.254 netmask 255.255.255.0 up

# Enable IP forwarding
#echo 1 > /proc/sys/net/ipv4/ip_forward

# Create a NAT firewall
iptables -I FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE

Cheers,

Herman

---

