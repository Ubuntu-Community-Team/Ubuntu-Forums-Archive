---
title: "OpenVPN Connected- No Internet nor LAN"
date: 2015-03-02
forum: Security
---

### Post by oatman2 on 2015-03-02
So I recently setup my OpenVPN server but when I connect to it I get neither LAN access nor Internet access. If I go into my browser I can access the server I'm connected to by typing: [http://192.168.2.150](http://192.168.2.150) and I'll get the Apache server. However if I try to access another IP in that subnet it will fail. Also if I attempt to access any other outside network it fails.
It might be important to note that my NIC on my server is bridged.

/etc/openvpn/server.conf
> port 1194
proto udp
dev tun
ca ca.crt
cert Daenerys.crt
key Daenerys.key  # This file should be kept secret
dh dh4096.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
;server-bridge
push "route 192.168.2.0 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

---

### Post by kevdog on 2015-03-03
Do you wanted a bridged or routed VPN -- your setup is for routed VPN.

Are your sure this line is correct: push "route 192.168.2.0 255.255.255.0"

Did you set up your firewall or kernel to allow for IP address forwarding?

---

### Post by oatman2 on 2015-03-03
> **kevdog said:**
> Do you wanted a bridged or routed VPN -- your setup is for routed VPN.

Are your sure this line is correct: push "route 192.168.2.0 255.255.255.0"

Did you set up your firewall or kernel to allow for IP address forwarding?

I set up my NIC as a bridge because I have a virtual machine running on it that monitors all the internet on my network. Also I'm not quite sure if the "route" section is correct. I only uncommented it because it looked right. Basically my IP Address are on 192.168.2.x locally where x starts at 101

---

### Post by kevdog on 2015-03-03
kernel forwarding is setup?  You're local IP range outside the VPN range is 192.168.2.x?

---

### Post by oatman2 on 2015-03-03
> **kevdog said:**
> kernel forwarding is setup?  You're local IP range outside the VPN range is 192.168.2.x?
Correct, yup.

---

