---
title: "OpenVPN and Tomcat"
date: 2012-06-21
forum: Server Platforms
---

### Post by jwright8 on 2012-06-21
I have an OpenVPN server that is working fine from outside connections on a Ubuntu machine with IpTables.

My client conf:
```

client
dev tap0
proto tcp
remote xxx.xxx.xxx.xxx 5556
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert hostname.crt
key hostname.key
ns-cert-type server
tls-auth ta.key 1
comp-lzo
verb 3

```

My server.conf:
```


port 5556


proto tcp

dev tap0

up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh /etc/openvpn/dh1024.pem
ifconfig-pool-persist ipp.txt



# (start=10.8.0.50 end=10.8.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
server-bridge 10.1.10.70 255.255.255.0 10.1.10.150 10.1.10.165

push "route 10.1.10.1 255.255.255.0"

keepalive 10 120

tls-auth ta.key 0 # This file is secret


comp-lzo

max-clients 15

user nobody
group nogroup
persist-key
persist-tun

status /var/log/openvpn-status.log 5
status-version 2



log-append /var/log/openvpn.log
log-append /var/log/openvpn.log

verb 4

tcp-queue-limit 256

```

I have a system that has Tomcat on it and hosts a Java webapp across the LAN.  When I am physically on the LAN, I can type 
```

\\CompName\index.html

```or
```

xxx.xxx.xxx.xxx/index.html

```by the IP.

When I connect over the VPN, however, I can't access the webapp.  I can mount the drive of the computer itself as a network drive.

When I go into the root webapp directory for tomcat, and I click index.html, it only shows the page title and the header and nothing else.  

Any help, or point in the right direction, would be greatly appreciated.



The following is an excerpt from my IpTables script:
```

## Default policies
#
iptables -P INPUT DROP
        # Drops all but approved input
iptables -P OUTPUT ACCEPT
        # See output filtering rules below
iptables -P FORWARD ACCEPT
        # Forward has to be set to accept for the connections to go through to the other side to the LAN
        # See forward filtering rules below


## Dropped forwarding ports
## For net access filtering
## For machines connected behind the Linux box
#
iptables -A FORWARD -p tcp --dport 21 -j DROP
iptables -A FORWARD -p tcp --dport 22 -j DROP
iptables -A FORWARD -p tcp --dport 23 -j DROP
iptables -A FORWARD -p tcp --dport 25 -j DROP
iptables -A FORWARD -p tcp --dport 43 -j DROP
iptables -A FORWARD -p tcp --dport 53 -j DROP
iptables -A FORWARD -p tcp --dport 79 -j DROP
iptables -A FORWARD -p tcp --dport 80 -j DROP # HTTP
iptables -A FORWARD -p tcp --dport 110 -j DROP
iptables -A FORWARD -p tcp --dport 115 -j DROP
iptables -A FORWARD -p tcp --dport 119 -j DROP
iptables -A FORWARD -p tcp --dport 143 -j DROP
iptables -A FORWARD -p tcp --dport 389 -j DROP
iptables -A FORWARD -p tcp --dport 443 -j DROP # HTTPS

```I assume that has something to do with it, though it appears Tomcat is listening on 80, 8005, and 8009.

It might also be worth mentioning that I am connecting from the outside with a Win 7 x86 client and am connecting to a Windows XP SP2 client on the LAN (that has the Tomcat installed).

The reason I posted here, other than you guys typically helping a lot more than others, is that I don't feel like it's a problem with Tomcat.  I feel like I have something configured wrong in my VPN.

Thanks in advance!

---

