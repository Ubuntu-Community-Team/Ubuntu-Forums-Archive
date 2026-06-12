---
title: "problems with openvpn in bridged mode on  ubuntu 12.04"
date: 2014-04-09
forum: Security
---

### Post by dreemzz on 2014-04-09
Hi 
I have a problem connecting two sites with openvpn on ubuntu  12.04 in bridged mode -the tunnel seems to be established, an ip address  is assigned to the client tap interface but when i try to ping a server  in the subnet on the other side i get an arp request incomplete. 
following the relevant configuration on the server side: 
in "/etc/network/interfaces" i have: 
 auto eth3 (WAN Interface)

iface eth3 inet static
address X.X.X.X
netmask 255.255.255.0
network X.X.X.X
broadcast X.X.X.X
gateway X.X.X.X

auto br1
iface br1 inet static
   address 10.10.47.251
   netmask 255.255.248.0
   network 10.10.40.0
   broadcast 10.10.47.255
   bridge_ports eth5.40
   bridge_fd 9
   bridge_hello 2
   bridge_maxage 12
   bridge_stp on
   bridge_prio 1000

in "/etc/openvpn/server40.conf" i have: 

 port 1195
proto udp
server-bridge 10.10.47.251 255.255.248.0 10.10.44.0 10.10.45.255
push "route 10.10.40.0 255.255.248.0"
dev tap1
ca ca.crt
cert blacknet.crt
tun-mtu 1454
key blacknet.key
dh dh1024.pem
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
ifconfig-pool-persist ipp.txt
keepalive 10 600
comp-lzo
persist-key
persist-tun
verb 3
mute 20
status openvpn-status.log
client-config-dir ccd
client-to-client

on the client side I have following configuration in "/etc/network/interfaces": 

 auto eth3 (WAN Interface)
iface eth3 inet static
address X.X.X.X
netmask 255.255.255.0
network X.X.X.X
broadcast X.X.X.X
gateway X.X.X.X

auto br1
iface br1 inet static
   address 10.10.47.250
   netmask 255.255.248.0
   network 10.10.40.0
   broadcast 10.10.47.255
   bridge_ports eth5.40
   bridge_fd 9
   bridge_hello 2
   bridge_maxage 12
   bridge_stp on
   bridge_prio 1000

and the client configuration for openvpn looks like the following: 

 client
remote X.X.X.X 1195
proto udp
dev tap1
reneg-sec 86400
auth-nocache
auth-retry interact
comp-lzo yes
verb 3
ca ca.crt
cert xcert.crt
key xkey.key

"ifconfig" on client looks like this: 

 tap1      Link encap:Ethernet  HWaddr ae:9c:0f:05:06:80  
         inet addr:10.10.44.0  Bcast:10.10.47.255  Mask:255.255.248.0
         inet6 addr: fe80::ac9c:fff:fe05:680/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:999 errors:0 dropped:0 overruns:0 frame:0
         TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:100 
         RX bytes:78851 (78.8 KB)  TX bytes:9813 (9.8 KB)

"arp -a" on the client looks like this: 

 ? (10.10.47.251) at <incomplete> on br1
"netstat -rn"  on client looks like: 
 10.10.40.0      10.10.47.251    255.255.248.0   UG        0 0          0 br1
10.10.40.0      0.0.0.0         255.255.248.0   U         0 0          0 br1
10.10.40.0      0.0.0.0         255.255.248.0   U         0 0          0 tap1

---

