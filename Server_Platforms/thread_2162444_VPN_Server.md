---
title: "VPN Server?"
date: 2013-07-14
forum: Server Platforms
---

### Post by d4m1r on 2013-07-14
Hey guys, got a question for you guys about setting up a VPN sever. I already have one up and running using OpenVPN but this second one I want to run is for a different purpose. The first is running on a VPS in a foreign country and I use it for some geolocated services available to those that have an IP from that country. It basically assigns me (the person connecting to the OpenVPN service) a random internal IP and then I am able to use its public IPv4 IP to surf the internet. 

This 2nd VPN server must serve a totally different purpose and I am not sure if OpenVPN again is the right choice, or something else, or if its even possibly at all with my setup? Basically, I will be going abroad for a few months and I want to be able to access my internal network at home. I have several LAN only devices (192.168.XXX...) that I would like to access from anywhere in the world and if I could grab my public IP from home and use it abroad too then bonus. I already have a server running Ubuntu 12.04 LTS (only LAMP currently) and DHCP is currently being served by my router. Everything on my network has static IPs ofcourse. Is OpenVPN the right choice and can I use that Ubuntu server to connect to internal LAN devices and even use my home IP address while abroad?

---

### Post by sandyd on 2013-07-14
> **d4m1r said:**
> Hey guys, got a question for you guys about setting up a VPN sever. I already have one up and running using OpenVPN but this second one I want to run is for a different purpose. The first is running on a VPS in a foreign country and I use it for some geolocated services available to those that have an IP from that country. It basically assigns me (the person connecting to the OpenVPN service) a random internal IP and then I am able to use its public IPv4 IP to surf the internet. 

This 2nd VPN server must serve a totally different purpose and I am not sure if OpenVPN again is the right choice, or something else, or if its even possibly at all with my setup? Basically, I will be going abroad for a few months and I want to be able to access my internal network at home. I have several LAN only devices (192.168.XXX...) that I would like to access from anywhere in the world and if I could grab my public IP from home and use it abroad too then bonus. I already have a server running Ubuntu 12.04 LTS (only LAMP currently) and DHCP is currently being served by my router. Everything on my network has static IPs ofcourse. Is OpenVPN the right choice and can I use that Ubuntu server to connect to internal LAN devices and even use my home IP address while abroad?
Set the options below in /etc/openvpn/server.conf, adjusting to your needs
```

#Level3 Nameservers
push "dhcp-option DNS 209.244.0.3"
push "dhcp-option DNS 209.244.0.4"
#Push all traffic through openvpn
push "redirect-gateway def1 bypass-dhcp"
#Push the 192.168.0.0 subnet to VPN client
push "route 192.168.0.0 255.255.255.0"

```

Make sure IP Forwarding (net.ipv4.ip_forward) is set to "1" in /etc/sysctl.conf

Make sure you have an iptables rule to route traffic to (ip is the static IP of your openvpn host)
```

-A POSTROUTING -s 192.168.10.0/24 -j SNAT --to-source 192.168.0.24
```

---

### Post by d4m1r on 2013-07-15
Awesome! But why would I use Level3 DNS? Could I not just use my ISPs and does it have to be public DNS? I can't just set my router to do the DNS?

Also to be clear "to-source 192.168.0.24" = static IP of my ubuntu server running OpenVPN and "-s 192.168.10.0/24" = my internal subnet range?

---

### Post by sandyd on 2013-07-15
> **d4m1r said:**
> Awesome! But why would I use Level3 DNS? Could I not just use my ISPs and does it have to be public DNS? I can't just set my router to do the DNS?

Also to be clear "to-source 192.168.0.24" = static IP of my ubuntu server running OpenVPN and "-s 192.168.10.0/24" = my internal subnet range?
You can use your own DNS servers - those are the values set in my OpenVPN Server just because my ISP doesn't have a DNS server

to the second question, yep

---

