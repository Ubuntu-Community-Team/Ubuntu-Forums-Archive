---
title: "Ubuntu Server 12.04.2 LTS Networking Issues with Multiple IPV4 Addresses"
date: 2013-06-22
forum: Server Platforms
---

### Post by westzilla on 2013-06-22
When I attempt to add additional IPs to the server and restart networking the following output is displayed for each of the additional ips added to the server. What does this mean?



root@server1:/home/bwest# /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... ssh stop/waiting
ssh start/running, process 4967
RTNETLINK answers: File exists
Failed to bring up eth0:0.
RTNETLINK answers: File exists
Failed to bring up eth0:1.
RTNETLINK answers: File exists
Failed to bring up eth0:2.
RTNETLINK answers: File exists
Failed to bring up eth0:3.
RTNETLINK answers: File exists
Failed to bring up eth0:4.
RTNETLINK answers: File exists
Failed to bring up eth0:5.
RTNETLINK answers: File exists
Failed to bring up eth0:6.
RTNETLINK answers: File exists
Failed to bring up eth0:7.
RTNETLINK answers: File exists
Failed to bring up eth0:8.
RTNETLINK answers: File exists
Failed to bring up eth0:9.
RTNETLINK answers: File exists
Failed to bring up eth0:10.
RTNETLINK answers: File exists
Failed to bring up eth0:11.
RTNETLINK answers: File exists
Failed to bring up eth0:12.
RTNETLINK answers: File exists
Failed to bring up eth0:13.
RTNETLINK answers: File exists
Failed to bring up eth0:14.
RTNETLINK answers: File exists
Failed to bring up eth0:15.
RTNETLINK answers: File exists
Failed to bring up eth0:16.
RTNETLINK answers: File exists
Failed to bring up eth0:17.
RTNETLINK answers: File exists
Failed to bring up eth0:18.
RTNETLINK answers: File exists
Failed to bring up eth0:19.
RTNETLINK answers: File exists
Failed to bring up eth0:20.
RTNETLINK answers: File exists
Failed to bring up eth0:21.
RTNETLINK answers: File exists
Failed to bring up eth0:22.
RTNETLINK answers: File exists
Failed to bring up eth0:23.
RTNETLINK answers: File exists
Failed to bring up eth0:24.
RTNETLINK answers: File exists
Failed to bring up eth0:25.
RTNETLINK answers: File exists
Failed to bring up eth0:26.
RTNETLINK answers: File exists
Failed to bring up eth0:27.
RTNETLINK answers: File exists
Failed to bring up eth0:28.
RTNETLINK answers: File exists
Failed to bring up eth0:29.
RTNETLINK answers: File exists
Failed to bring up eth0:30.
RTNETLINK answers: File exists
Failed to bring up eth0:31.
RTNETLINK answers: File exists
Failed to bring up eth0:32.
RTNETLINK answers: File exists
Failed to bring up eth0:33.
[ OK ]
root@server1:/home/bwest#

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 198.27.66.143
netmask 255.255.255.0
network 198.27.66.0
broadcast 198.27.66.255
gateway 198.27.66.254

auto eth0:0
iface eth0:0 inet static
address 198.50.158.112
netmask 255.255.255.0
network 198.50.158.0
broadcast 198.50.158.255
gateway 198.27.66.254
auto eth0:1
iface eth0:1 inet static
address 198.50.158.113
netmask 255.255.255.0
network 198.50.158.0
broadcast 198.50.158.255
gateway 198.27.66.254
auto eth0:2
iface eth0:2 inet static
address 198.50.158.114
netmask 255.255.255.0
network 198.50.158.0
broadcast 198.50.158.255
gateway 198.27.66.254
auto eth0:3
iface eth0:3 inet static
address 198.50.230.32
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:4
iface eth0:4 inet static
address 198.50.230.33
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:5
iface eth0:5 inet static
address 198.50.230.34
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:6
iface eth0:6 inet static
address 198.50.230.35
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:7
iface eth0:7 inet static
address 198.50.230.36
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:8
iface eth0:8 inet static
address 198.50.230.37
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:9
iface eth0:9 inet static
address 198.50.230.38
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:10
iface eth0:10 inet static
address 198.50.230.39
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:11
iface eth0:11 inet static
address 198.50.230.40
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:12
iface eth0:12 inet static
address 198.50.230.41
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:13
iface eth0:13 inet static
address 198.50.230.42
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:14
iface eth0:14 inet static
address 198.50.230.43
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:15
iface eth0:15 inet static
address 198.50.230.44
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:16
iface eth0:16 inet static
address 198.50.230.45
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:17
iface eth0:17 inet static
address 198.50.230.46
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:18
iface eth0:18 inet static
address 198.50.230.47
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:19
iface eth0:19 inet static
address 198.50.230.48
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:20
iface eth0:20 inet static
address 198.50.230.49
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:21
iface eth0:21 inet static
address 198.50.230.50
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:22
iface eth0:22 inet static
address 198.50.230.51
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:23
iface eth0:23 inet static
address 198.50.230.52
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:24
iface eth0:24 inet static
address 198.50.230.53
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:25
iface eth0:25 inet static
address 198.50.230.54
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:26
iface eth0:26 inet static
address 198.50.230.55
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:27
iface eth0:27 inet static
address 198.50.230.56
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:28
iface eth0:28 inet static
address 198.50.230.57
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:29
iface eth0:29 inet static
address 198.50.230.58
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:30
iface eth0:30 inet static
address 198.50.230.59
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:31
iface eth0:31 inet static
address 198.50.230.60
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:32
iface eth0:32 inet static
address 198.50.230.61
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254
auto eth0:33
iface eth0:33 inet static
address 198.50.230.63
netmask 255.255.255.0
network 198.50.230.0
broadcast 198.50.230.255
gateway 198.27.66.254

root@server1:/home/bwest# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 198.27.66.254 0.0.0.0 UG 100 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
198.27.66.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
198.50.158.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
198.50.230.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0

root@server1:/home/bwest# nano /etc/hosts

# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1 localhost.localdomain localhost
198.27.66.143 server1.westzilla.com server1
2607:5300:60:1B8f::1 server1.westzilla.com server1

# The following lines are desirable for IPv6 capable hosts
#(added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

root@server1:/home/bwest# nano /etc/resolv.conf

nameserver 127.0.0.1
nameserver 213.186.33.99
search ovh.net


any thoughts would be helpful all added ips are routed to the servers base ip of 198.27.66.143 and all ips seem to be functional but when networking starts/restarts the above is displayed

thanks

---

### Post by darkod on 2013-06-22
Have you tried specifying only address, network and broadcast for all the additional interfaces?

It will automatically use the gateway from eth0. I know it works for subsecuent IPs, not sure in your case because all the IPs are not part of one group only. But give it a shot. Drop the netmask and gateway from all the eth0:N interfaces.

---

### Post by newbie-user on 2013-06-23
You've gotta go back and check your subnetting. First of all, you should only have one gateway, which should be your default gateway. So delete all those gateway lines. Second thing is none of your virtual NICs can reach the 198.27.66.254 gateway anyway with a netmask of 255.255.255.0. Furthermore, all your IP addresses are routable IPs. Are your sure your ISP gave you all those IPs with three sets of /24 networks?

---

