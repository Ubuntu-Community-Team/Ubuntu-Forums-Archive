---
title: "Invisible configured public IP of ubuntu 16.04 lts"
date: 2017-08-01
forum: Server Platforms
---

### Post by poliman-pl on 2017-08-01
I have configured two network interfaces in my server based on Ubuntu 16.04 LTS. Below is configuration from /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp1s0 enp2s0
iface enp1s0 inet static
        address 192.168.100.206
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        #gateway 192.168.100.2
        #dns-nameservers 192.168.100.2

iface enp2s0 inet static
        address X.X.X.181
        network X.X.X.176
        netmask 255.255.255.248
        gateway X.X.X.177
        dns-nameservers Y.Y.Y.Y Z.Z.Z.Z

```
Below is routing table:
```
sadmin@scolo006:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         X.X.X.177  0.0.0.0         UG    0      0        0 enp2s0
X.X.X.176  0.0.0.0         255.255.255.248 U     0      0        0 enp2s0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
```
```
sadmin@scolo006:~$ ip route
default via X.X.X.177 dev enp2s0 onlink
X.X.X.176/29 dev enp2s0  proto kernel  scope link  src X.X.X.181
192.168.100.0/24 dev enp1s0  proto kernel  scope link  src 192.168.100.206

```
I can ping public interface (ping command executed from this server, it's his public interface):
```
sadmin@scolo006:~$ ping X.X.X.181
PING X.X.X.181 (X.X.X.181) 56(84) bytes of data.
64 bytes from X.X.X.181: icmp_seq=1 ttl=64 time=0.027 ms
^C
--- X.X.X.181 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.027/0.027/0.027/0.000 ms
```
But I can't ping gateway, google.com, 8.8.8.8, one word - anything:
```
sadmin@scolo006:~$ ping google.com
ping: unknown host google.com
sadmin@scolo006:~$ ping X.X.X.177
PING X.X.X.177 (X.X.X.177) 56(84) bytes of data.
From X.X.X.181 icmp_seq=1 Destination Host Unreachable
From X.X.X.181 icmp_seq=2 Destination Host Unreachable
From X.X.X.181 icmp_seq=3 Destination Host Unreachable
^C
--- X.X.X.177 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3016ms
pipe 3
sadmin@scolo006:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From X.X.X.181 icmp_seq=1 Destination Host Unreachable
From X.X.X.181 icmp_seq=2 Destination Host Unreachable
From X.X.X.181 icmp_seq=3 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3013ms
pipe 3

```

I have one more Linux server based on Ubuntu 14.04. There "ip route" gives a little another output - there isn't "onlink":
```
default via X.X.X.177 dev em4
```
Other things like routing table looks identical. Of course from second server I can ping gateway, it has internet connection, etc. No idea what is wrong...

---

### Post by darkod on 2017-08-01
Are the cables into port 1 and 2 connected correctly? Make sure the cable for the public interface is really connected to the public interface.
At first look the config looks correct. Are you using any firewall?

---

### Post by Paul Weaver on 2017-08-04
P.S. I don't think network and braodcast are needed - I never put them in

I think you have a router and two servers on the same network right? 

Assuming your router is 1.1.1.177/29 and you are 1.1.1.181 and the other server is 1.1.1.182

Can you ping the other server (.182)? 

Are you sure that your cable is plugged into your router, right vlan etc (swap the two cables)

If you run tcpdump on the 1.1.1.181 interface, do you see any traffic like lldp from the router, or arps? You should see outgoing arps.

If you run tcpdump on the 1.1.1.182 server, do you see any arps from the mac address of 1.1.1.181

If you run the two servers back-to-back can they ping each other?

When you run "ping 1.1.1.177", the first thing that happens is linux decides that IP is on a directly connected network as it's in the routing table (enp2s0 in this case), then sends out an ARP request which says "who has 1.1.1.177, tell 1.1.1.181"

The router should then respond with a mac address - "1.1.1.181 is as aa:bb:cc:dd:ee:ff"

Linux then goes "great, I'll create a packet with that destination mac address" and dumps it onto the network

If you were to ping 8.8.8.8, linux works out it's not on a directly connected network, and thus sends it to the most appropiate gateway - 1.1.1.181 in this case, to do that it sends an ARP out as above.

Only when the arp entry is in the local arp cache (run arp -an to see it), will it be able to skip that first stage.

---

### Post by poliman-pl on 2017-08-07
@darkod
Cables are toughly put in to sockets. ;) When I remove local interface cable "ping" from other computer is break, after put in again it is nice. Of course I don't use firewall currently for testing purposes.

@Paul Weaver
Both servers stay near each other in one "rack". You have right, router has ip .177, one server .180 and another one .181. From one with .181 I can't ping anything except this (WAN) interface with .181 address. From second one (with .180) I can ping anything I want from Internet and from range of IP adresses from which are both server's public interfeces.
I tried swap cables - not help.
From which server should I execute tcpdump with X.X.X.180 and X.X.X.181 - this one with broken internet access? How should look tcpdump command in this case - tcpdump -i enp2s0 src X.X.X.180 ?
Result of "arp -an":
```
sadmin@scolo006:~$ arp -an
? (192.168.100.246) at <incomplete> on enp1s0
? (192.168.100.253) at 10:08:b1:d8:cb:99 [ether] on enp1s0
? (192.168.100.122) at 74:d4:35:10:b0:36 [ether] on enp1s0
? (X.X.X.177) at <incomplete> on enp2s0
? (192.168.100.125) at 90:2b:34:e4:07:9c [ether] on enp1s0
? (192.168.100.204) at d0:50:99:09:c8:32 [ether] on enp1s0
? (192.168.100.202) at d8:9d:67:2a:c9:18 [ether] on enp1s0
```

What do You mean "If you run the two servers back-to-back can they ping each other?" - should I connect them directly in lan/wan interfaces using rj45 cable?

PS
Guys, do You know what is "onlink" in output of "ip route" command and why on one server it is (this one without internet connection) but on second one (with internet connection) it isn't? Btw servers are near each other in one rack. I am confused and I am affraid it's not a problem with configuration but something with physical connecting/cables.

---

### Post by darkod on 2017-08-08
Have you tried using separate 'auto' commands in the interfaces definition? Inever put both interfaces in the same line. Try separate auto enp2so before the iface line and reboot the server.
After that check again. The config looks correct, you might have issues with the network cable or the network switch. Double check the whole setup. If you are using both public and private subnets that means the switches have to be configured correctly for that.

---

### Post by poliman-pl on 2017-08-10
@darkod
You have right mate. I checked again connection with switch and there was a problem... Now both servers have internet/WAN connection. Finally I am happy. Nathless appreciate Your answers/advices. I will remember about them when I reach some network problems. What is the difference between ```
auto enp1s0 enp2s0
``` and 
```
auto enp1s0
auto enp2s0
``` ? Some times ago on some linux forum I got information that "auto interface_name interface2_name" etc. is ok form.

---

