---
title: "OpenVPN:  Cannot get internet traffic to route through vpn connection"
date: 2008-06-30
forum: Server Platforms
---

### Post by vital101 on 2008-06-30
Hey everyone,

I recently set up an openVPN server at home.  I have the client and server configured well enough that the vpn connection can be made, and that I can connect to other machines on my network.  However, if I try to connect to machines outside of the network that the vpn is on, it won't work.

My server.conf:
```

# Which local IP address should OpenVPN 
# listen on? (optional) 
local 192.168.1.101
port 1194
# TCP or UDP server? 
proto udp 
#This is key to configuring our bridge 
dev tap0 
#direct these to your generated files 
ca /etc/openvpn/examples/easy-rsa/2.0/keys/ca.crt 
cert /etc/openvpn/examples/easy-rsa/2.0/keys/server.crt 
key /etc/openvpn/examples/easy-rsa/2.0/keys/server.key   
dh /etc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem 
ifconfig-pool-persist ipp.txt 
#ensure the range of ip addresses you use in the last  two arguments 
# of this statement are not in use by  either the DHCP server or any other
# device on your  internal network. 
server-bridge 192.168.1.125 255.255.255.0 192.168.1.130 192.168.1.140 
#needed to allow communication to internal network 
client-to-client 
keepalive 10 120 
#encryption - very important ;) 
#AES encryption is backed by many security firms
#however if you are concerned about speed use blowfish: "BF-CB"
cipher AES-128-CBC  
#if you have another subnet you need to provide the route
#push "route 173.23.2.0 255.255.255.0"
#server id protection
tls-auth ca.key 0
#compression for network speed 
comp-lzo 
# if packets are too large fragment them (only really useful if you have an old router) 
#fragment 1400 
#limit the number of connections
max-clients 5
#some secuurity settings 
# do not use if running server on Windows
user nobody 
group nogroup 
persist-key 
persist-tun 
#log file settings 
status openvpn-status.log 
verb 3 
# authentication plugin
#forces client to have a linux acount in order to connect
plugin /usr/lib/openvpn/openvpn-auth-pam.so login 

```

My client.conf
```

client 
dev tap 
proto udp 
# change this to your server's address 
remote xxx.xxx.xxx.xxx 1194 
resolv-retry infinite 
nobind
persist-key 
persist-tun 
# Point the key and crt files to  
# the ones for this user 
tls-client
ca ca.crt 
cert jack.crt 
key jack.key 
#ensure that we are talking to a server 
ns-cert-type server
#confirm we are talking to the correct server 
tls-auth ca.key 1
# Select a cryptographic cipher. 
# If the cipher option is used on the server 
# then you must also specify it here. 
cipher AES-128-CBC 
# Enable compression on the VPN link. 
comp-lzo 
#fragment large packets 
# I found I needed this for some games but it is 
# not required
#fragment 1400  
# enable user/pass authentication
auth-user-pass

```

I haven't done anything with the routing tables as I'm afraid to mess with them.  Any help would be much appreciated with this. Thanks!

---

### Post by Lieter on 2008-11-26
I have the same problem ([http://ubuntuforums.org/showthread.php?t=465581](http://ubuntuforums.org/showthread.php?t=465581)), i was wondering if you have it working now and if so, how?

---

### Post by obg123 on 2008-11-26
I have no idea about this particular VPN solution, but I would suggest taking a close look at the routing table. What does route -n output? My guess is that your config does not need external traffic to go through VPN and then out, right? Verify that only VPN-traffic is routed through the VPN (ipsec?) interface.

---

