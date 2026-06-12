---
title: "Configuring 3 ETH on ubunut server - not working"
date: 2013-09-11
forum: Server Platforms
---

### Post by calloni-gianluca on 2013-09-11
Hi to all experts... And sorry for my english,...

I need a little help..

The situation:

[LIST]
[*]VMWARE ESXi5
[*]A virtual machine UBUNTU server 12.04.2. with 3 eth (eth0 - eth1 - eth2)
[LIST]
[*]eth0 => ADSL n. 1 for pc client navigation under squid => working fine
[*]eth1 => Local Lan
[*]eth2 => ADSL n.2 (new) only for incoming connection on http (80)
[/LIST]
[/LIST]
all the network card are correctly configured in /etc/network/interfaces, with static ip address, network/broadcast address and gateway (only eth0 and eth2)

Well.. i'm not able to connect from out of my local lan on the eth2 (ping or http....)

I've tested this connection on another virtual machine (win xp) and work fine with the same configuration.

Someone could help me to solve this problem?

Thank's in advance to all

---

### Post by calloni-gianluca on 2013-09-23
I try to give some more information:

```

eth0 => ADSL 1    => 94.xxx.xxx.150 / 28
eth1 => Local Lan => 10.1.1.120 / 24
eth2 => ADSL 2    => 130.xxx.xxx.2 / 30
```

my **/etc/network/interfaces**
  ```
# The loopback network interface
auto lo eth0 eth1 eth2 
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 94.xxx.xxx.150
        netmask 255.255.255.240
        network 94.xxx.xxx.144
        broadcast 94.xxx.xxx.159
        dns-nameservers 127.0.0.1 8.8.8.8 8.8.4.4 100.1.1.120
        post-up iptables-restore < /etc/iptables.up.rules
        gateway 94.xxx.xxx.145
        dns-domain xxxxxxx.local 


iface eth1 inet static
        address 100.1.1.120
        netmask 255.255.255.0
        network 100.1.1.0
        broadcast 100.1.1.255


iface eth2 inet static
        address 130.xxx.xxx.2
        netmask 255.255.255.252
        broadcast 130.xxx.xxx.3
        network 130.xxx.xxx.0

```

my **netstat -rn**
  ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         94.xxx.xxx.145  0.0.0.0         UG        0 0          0 eth0
94.xxx.xxx.144  0.0.0.0         255.255.255.240 U         0 0          0 eth0
10.1.1.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
130.xxx.xxx.0   0.0.0.0         255.255.255.252 U         0 0          0 eth2

```  From internet i can ping eth0 on 94.xxx.xxx.150. I'm not able to ping 130.xxx.xxx.2 on eth2.
  I try to run **tcpdump -n -i eth2 icmp** and ping 130.xxx.xxx.2 from internet. The output is:
  ```
17:25:01.365457 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 1, length 64
17:25:02.313759 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 2, length 64
17:25:03.321676 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 3, length 64
17:25:04.323308 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 4, length 64
17:25:05.342715 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 5, length 64
17:25:06.343482 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 6, length 64
17:25:07.354359 IP 5.91.118.109 > 130.0.149.2: ICMP echo request, id 30552, seq 7, length 64

```  Otherways, if i try to ping 94.xxx.xxx.150 on eth0 all seems fine:
  ```
17:27:42.957262 IP 5.91.118.109 > 94.90.104.150: ICMP echo request, id 4185, seq 1, length 64
17:27:42.957340 IP 94.90.104.150 > 5.91.118.109: ICMP echo reply, id 4185, seq 1, length 64
17:27:43.540061 IP 5.91.118.109 > 94.90.104.150: ICMP echo request, id 4185, seq 2, length 64
17:27:43.540116 IP 94.90.104.150 > 5.91.118.109: ICMP echo reply, id 4185, seq 2, length 64
17:27:44.545820 IP 5.91.118.109 > 94.90.104.150: ICMP echo request, id 4185, seq 3, length 64
17:27:44.545847 IP 94.90.104.150 > 5.91.118.109: ICMP echo reply, id 4185, seq 3, length 64

```  someone can help me to understand where i make mistake? And why?

---

### Post by SeijiSensei on 2013-09-23
Do you have packet forwarding enabled in the kernel?  Look at the comments in /etc/sysctl.conf about the net.ipv4.ip_forward control.  Windows probably doesn't care about security enough to block packet forwarding by default the way most Linux distributions now do.

---

### Post by houstonbofh on 2013-09-23
You do not have any kind of route for the secondary interface, so a pibg is comming in on that interface, and going out the other one and failing as the IP has changed.  Dual WAN is complex.  Are you sure you need this on the server and can not just use an appliance for the dual wan?  (Like pfSense, for example)

---

