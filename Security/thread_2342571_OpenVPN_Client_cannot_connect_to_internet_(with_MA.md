---
title: "OpenVPN Client cannot connect to internet (with MASQUERADE iptables)"
date: 2016-11-07
forum: Security
---

### Post by xplot1on on 2016-11-07
Once the client Connect to OpenVPN service, Internet access is not possible. I have MASQUERADE between tun interface and eth interface and also forward the Server's public IP so applications that requires access using Public IP can continue to function when openvpn is in use on client side as well as access to internal networks (As seen in the server config)

netstat -rn (OpenVPN Killed)
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         128.199.64.1    0.0.0.0         UG        0 0          0 eth0
10.15.0.0       0.0.0.0         255.255.0.0     U         0 0          0 eth0
10.130.0.0      0.0.0.0         255.255.0.0     U         0 0          0 eth1
128.199.64.0    0.0.0.0         255.255.192.0   U         0 0          0 eth0

```

netstat -rn (OpenVPN Running)

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         128.199.64.1    0.0.0.0         UG        0 0          0 eth0
10.15.0.0       0.0.0.0         255.255.0.0     U         0 0          0 eth0
10.130.0.0      0.0.0.0         255.255.0.0     U         0 0          0 eth1
128.199.64.0    0.0.0.0         255.255.192.0   U         0 0          0 eth0
192.168.94.0    192.168.94.2    255.255.255.0   UG        0 0          0 tun0
192.168.94.2    0.0.0.0         255.255.255.255 UH        0 0          0 tun0

```

And my OpenVPN Server config
```

port 443
# TCP or UDP server?
proto tcp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 192.168.94.0 255.255.255.0
ifconfig-pool-persist ipp.txt
#############################################################
# redirect all default traffic via the VPN                  #
#   redirect-gateway def1                                   #
# redirect the home network 192.168.1/24 via the VPN        #
#   route 192.168.1.0 255.255.255.0                         #
# redirect another network to NOT go via the VPN            #
#   route 10.10.0.0 255.255.255.0 net_gateway               #
# redirect a host using a domain name to NOT go via the VPN #
#   route www.google.be 255.255.255.255 net_gateway         #
#############################################################

#route 128.199.115.157 255.255.192.0 net_gateway
push "route 128.199.115.157 255.255.192.0"

# Routing for Home Network
push "route 192.168.2.0 255.255.255.0"

# Routing for Internal Network
push "route 10.27.8.20 255.255.255.255 net_gateway"

push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
;client-to-client
;duplicate-cn
keepalive 10 120
comp-lzo
;max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
;log         openvpn.log
;log-append  openvpn.log
verb 3

```

---

