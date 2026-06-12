---
title: "KVM client as router, virtual nic won't forward packets"
date: 2013-04-08
forum: Virtualisation
---

### Post by Matteus_Blanc on 2013-04-08
All the machines mentioned below are Ubuntu 10.04

I have a simple home network with a gateway machine - Pig - which has twin nics, one connecting to the router/modem and out while  the other connects to a switch to feed the home network.

> WAN
   ||
 ############  192.168.0.1
 # router/modem #
 ############--
                                     |
                                 ##### 192.168.0.100 (br1) & 192.168.192.1(br0)
                                 # PIG #
                                  #####
                                        |
                                        |
                                   ######## 192.168.192.0/24
                                   # SWITCH #
                                   ########
                                         |
                                       LAN

Pig runs a bunch of servers (DHCP, DNS coupled as DDNS, KDC, VPN etc) to feed the network, acts a default route out and provides a large nfs share on an LVM. It also hosts KVM clients which sit on the same LAN and connect using the bridged br0. These vms sit on the LVM and share an nfs /home. Everything works.

A few weeks back I decided to virtualise Pig into one of the KVM clients. I did this to make backup/recovery and migration simpler. I use three letter animals for physical machines on the network and four letter animals for vms, so the virtual pig was designated the name boar. I broke the VPN out separately to another client called duck. The virtualisation was very simple to achieve using rsync. It worked fine.

Now duck does exactly what I'd expect. It connects to the vpn(s) and forwards packets. Any clients on the network wanting to get to the vpn 10.11.12.0/24 use a duck route via the default route i.e. the gateway machine has a route to send 10.11.12.0/24 traffic to duck. It mimics what pig did. The duck iptables and kernel routing table are shown below:

> $sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.192.0/24     anywhere            
MASQUERADE  all  --  10.11.12.0/24        anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.185.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun1
10.11.12.1      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
XXX.XXX.XXX.XXX   192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
10.185.1.1      10.185.1.5      255.255.255.255 UGH   0      0        0 tun1
XXX.XXX.XXX.XXX     192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX   192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX   192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX   192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX   192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX 192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
XXX.XXX.XXX.XXX 192.168.192.1   255.255.255.255 UGH   0      0        0 eth0
192.168.192.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.11.12.0      10.11.12.1      255.255.255.0   UG    0      0        0 tun0
0.0.0.0         10.185.1.5      0.0.0.0         UG    0      0        0 tun1

 As you can see there are two vpns and I am using one as the default route. This all works. The point being that the vm will packet forward to the tun interfaces.

The problem is that I am unable to set boar as the new gateway machine because, despite setting the masquerade and packet forwarding identically to pig, packets are never forwarded/returned to the WAN. It seems like the virtual nics won't allow boar to act as the gateway. I bridged both vnics to mimic pig but packets don't get forwarded and I can't figure out why. Interestingly when boar is acting as the gateway it will correctly forward 10.11.12.0/24 traffic to duck. So it's just connections over the virtual nics set up by libvirt.

Boar iptables, kernel routing table, packet forwarding: (DOESN'T WORK):confused:
> @boar ~
$sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.0.0/16       anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

@boar ~
$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.192.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0-br
10.11.12.0      duck   255.255.255.0   UG    0      0        0 eth0-br
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1-br
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0-br
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1-br

@boar ~
$cat /proc/sys/net/ipv4/ip_forward
1

@boar ~
$ping google.com
PING google.com (173.194.34.137) 56(84) bytes of data.
64 bytes from lhr14s21-in-f9.1e100.net (173.194.34.137): icmp_seq=1 ttl=55 time=42.6 ms
64 bytes from lhr14s21-in-f9.1e100.net (173.194.34.137): icmp_seq=2 ttl=55 time=24.7 ms
64 bytes from lhr14s21-in-f9.1e100.net (173.194.34.137): icmp_seq=3 ttl=55 time=50.5 ms
64 bytes from lhr14s21-in-f9.1e100.net (173.194.34.137): icmp_seq=4 ttl=55 time=16.7 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3019ms
rtt min/avg/max/mdev = 16.789/33.661/50.527/13.499 ms

boar has static ips on both networks as 192.168.0.101 and 192.168.192.2 respectively. So it's as close to pig as it can be

same thing for pig (WORKS)

> @pig ~
$sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.192.0/24     anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

@pig ~
$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
255.255.255.255 0.0.0.0         255.255.255.255 UH    0      0        0 br0
192.168.192.0   0.0.0.0         255.255.255.0   U     0      0        0 br0
10.11.12.0      duck   255.255.255.0   UG    0      0        0 br0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 br1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 br1

@pig ~
$cat /proc/sys/net/ipv4/ip_forward
1

So, although pig and boar are identically configured, I can use pig as the default route out but not boar. If boar is set as the default route then packets don't get out. I can't hit the WAN or even the router on 192.168.0.1 from any clients other than boar iteself. 

Weird eh? I'd appreciate some help from anyone who knows more about this than me.

By the way I realise there is a slight difference in the masquerade rules - this is deliberate on my part and due to testing various theories. I also appreciate for performance reasons it makes more sense for the pig to remain the gateway. But I still want to understand why I can't get boar to do what I want.

I haven't provided /etc/network/interfaces or the output from ifconfig or the INPUT chain rules but I can assure you that they are the same - cause boar is a clone of pig. Pings, tracepath, mtr all just hang after hitting boar. I've also tried setting up boar with one nic and pointing that to pig. Same deal, it all works from within boar but as soon as you try and route through boar from another client it doesn't work.

---

