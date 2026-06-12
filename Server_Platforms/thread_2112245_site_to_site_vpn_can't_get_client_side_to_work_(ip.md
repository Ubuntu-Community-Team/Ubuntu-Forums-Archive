---
title: "site to site vpn: can't get client side to work (iptables/routing?)"
date: 2013-02-04
forum: Server Platforms
---

### Post by i2so4 on 2013-02-04
Hi

i'm trying to link 2 networks via VPN tunnel. let me describe my network layout(s):

"main" site: 192.168.1.0/24 (router is .1, VPN server is .6)
"branch" site: 192.168.3.0/24 (router is .1, VPN client is .3)
192.168.3.3: eth0 - internal network; tun0 - VPN tunnel

at the moment i can access any computer from VPN clients CLI (VPN itself is working). however i cannot access anything in the 192.168.1.0/24 subnet from other 192.168.3.0/24 computers. 

on vpn client, if i run "tcpdump -nnvvXSs 0 icmp -i eth0", i can see that packets are routed correctly to the VPN client machine, but running the same command on tun0 interface shows nothing. i therefore suspect, that the problem is in the internal routing of the vpn client machine.
i have tried to fiddle with iptables but since i know pretty much nothing of it, no success. 

any ideas/links/additional questions?

---

### Post by furything on 2013-02-04
Hi
Please can yo provide more info?
What is the output from?```
sudo iptables -v -x -n -L
```

What is your subnet mask for lans 255.255.255.0 or 255.255.0.0?

---

### Post by i2so4 on 2013-02-04
```
# iptables -v -x -n -L
Chain INPUT (policy ACCEPT 15 packets, 1005 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  tun0   eth0    0.0.0.0/0            192.168.3.0/24
       0        0 ACCEPT     all  --  eth0   tun0    0.0.0.0/0            192.168.1.0/24

Chain OUTPUT (policy ACCEPT 8 packets, 1056 bytes)
    pkts      bytes target     prot opt in     out     source               destination

```
subnet masks are both 255.255.255.0
with these rules in ipchains i can see, that packets DO enter tun0, however i see no traffic on the servers tun0 interface (i assume that this is how a VPN tunnel works: goes in from here and comes out on the other end)

---

### Post by darkod on 2013-02-04
I have no experience setting an ubuntu machine to be VPN server, but usually for forwarding packets between interfaces you need to enable it first. Did you do that?

I assume the same applies to tun0 even when it's not "physical" interface.

Open /etc/sysctl.conf and look for a line like:
#net.ipv4.ip_forward=1

Remove the # symbol to enable it. Save and close the file. Restart networking or the server.

Also, make sure iptables has the forward policy to ACCEPT, or if you want DROP then create rules to allow your traffic. I suggest to test with ACCEPT policy first, you can close it down later. The setting will depend on how you load iptables at boot.

EDIT PS: I just noticed above the forward policy is ACCEPT, so that should not block you.

---

### Post by SeijiSensei on 2013-02-04
Show us the routing tables on the machines at each end of the tunnel by running the command "route -n".  I suspect you're just missing a route somewhere.

If this is OpenVPN, do you have an "up" statement in each configuration to run a routing script when the tunnel starts?

If this is a point-to-point route, I strongly recommend that the VPN interfaces have IP addresses in a subnet other than ones you are using on the host machines.  Use something like 10.0.0.1/24 and 10.0.0.2/24 for the VPN endpoint addresses.  It makes routing much easier since you can add a route like this on 192.168.3.3:

```
ip route add 192.168.1.0/24 via 10.0.0.1
```

and vice versa.

---

### Post by i2so4 on 2013-02-04
Hello

i got this working by messing with server configuration ([this link]("http://www.secure-computing.net/wiki/index.php/OpenVPN/Routing"))

it seems that the problem was missing "iroute" on server side client config

for future help seekers, full config :)

openVPN server config: 
```
rait@vpn:~$ cat /etc/openvpn/client-config/eee901
iroute 192.168.3.0 255.255.255.0
rait@vpn:~$ cat /etc/openvpn/server.conf
local 192.168.1.6
port 1194
proto udp
dev tun
ca ca.crt
cert vpn.crt
key vpn.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.0 255.255.255.0"
route 192.168.3.0 255.255.255.0
client-config-dir client-config
client-to-client
keepalive 10 120
comp-lzo
persist-key
status openvpn-status.log
verb 3

```

openVPN client config:
```
root@eee901:~# cat /etc/openvpn/client.conf
client
dev tun
proto udp
remote <-- enter your server-address --> 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert eee901.crt
key eee901.key
ns-cert-type server
comp-lzo
verb 3
pull
```

routing tables on server:
```
rait@vpn:~$ route -n
Tuuma IP ruutingutabel
Sihtpunkt       Ruuter          V&#262;µrgumask       Lipud Meetr  Mitu Kasut Liides
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.3.0     10.8.0.2        255.255.255.0   UG    0      0        0 tun0

```

routing tables on client:
```
root@eee901:~# route -n
Tuuma IP ruutingutabel
Sihtpunkt       Ruuter          V&#262;µrgumask       Lipud Meetr  Mitu Kasut Liides
0.0.0.0         192.168.3.1     0.0.0.0         UG    100    0        0 eth0
10.8.0.0        10.8.0.21       255.255.255.0   UG    0      0        0 tun0
10.8.0.21       0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     10.8.0.21       255.255.255.0   UG    0      0        0 tun0
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

interfaces on server:
```
rait@vpn:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.6
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        post-up iptables-restore < /etc/iptables.rules

```

interfaces on client:
```
rait@eee901:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.3.3
        network 192.168.3.0
        netmask 255.255.255.0
        broadcast 192.168.3.255
        gateway 192.168.3.1
        post-up iptables-restore < /etc/iptables.rules

```

iptables on server:
```
rait@vpn:~$ cat /etc/iptables.rules
# Generated by iptables-save v1.4.12 on Tue Feb  5 00:58:16 2013
*filter
:INPUT ACCEPT [251:26480]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [178:25962]
-A FORWARD -d 192.168.1.0/24 -i tun0 -o eth0 -j ACCEPT
-A FORWARD -d 192.168.3.0/24 -i eth0 -o tun0 -j ACCEPT
COMMIT
# Completed on Tue Feb  5 00:58:16 2013

```

iptables on client:
```
rait@eee901:~$ cat /etc/iptables.rules
# Generated by iptables-save v1.4.12 on Tue Feb  5 01:11:34 2013
*filter
:INPUT ACCEPT [26587:2650915]
:FORWARD ACCEPT [986:59160]
:OUTPUT ACCEPT [36599:5032240]
-A FORWARD -d 192.168.3.0/24 -i tun0 -o eth0 -j ACCEPT
-A FORWARD -d 192.168.1.0/24 -i eth0 -o tun0 -j ACCEPT
COMMIT
# Completed on Tue Feb  5 01:11:34 2013

```

don't forget to enable forwarding in kernel
hope this helps someone someday :)
and thanks for help guys

---

