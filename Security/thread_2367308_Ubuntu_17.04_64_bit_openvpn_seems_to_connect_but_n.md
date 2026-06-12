---
title: "Ubuntu 17.04 64 bit openvpn seems to connect but not working"
date: 2017-07-28
forum: Security
---

### Post by palazzo2 on 2017-07-28
Hello,

When I click on VPN Connections->myvpn name, it logins successfully. I can access internet, but not my company's services. I can't browse JIRA, use webmail. So OpenVPN is not working:D Can someone please help?  Here's my system output after connecting to VPN:

```

ifconfig

enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:e1:ad:22:d3:56  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf2300000-f2320000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 730  bytes 55762 (55.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 730  bytes 55762 (55.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.77.96.207  netmask 255.255.248.0  broadcast 10.77.103.255
        inet6 fe80::1eec:a89:5f83:b642  prefixlen 64  scopeid 0x20<link>
        ether f8:59:71:31:e5:d4  txqueuelen 1000  (Ethernet)
        RX packets 626494  bytes 623297970 (623.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 217648  bytes 30416975 (30.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.77.96.1      0.0.0.0         UG    600    0        0 wlp3s0
10.77.96.0      0.0.0.0         255.255.248.0   U     600    0        0 wlp3s0
10.77.96.1      0.0.0.0         255.255.255.255 UH    600    0        0 wlp3s0
62.154.227.96   0.0.0.0         255.255.255.240 U     50     0        0 tun0
62.157.227.32   0.0.0.0         255.255.255.248 U     50     0        0 tun0
77.246.120.176  0.0.0.0         255.255.255.240 U     50     0        0 tun0
77.249.120.176  0.0.0.0         255.255.255.240 U     50     0        0 tun0
80.149.217.96   0.0.0.0         255.255.255.224 U     50     0        0 tun0
80.150.81.224   0.0.0.0         255.255.255.240 U     50     0        0 tun0
80.157.235.32   0.0.0.0         255.255.255.240 U     50     0        0 tun0
82.119.168.176  0.0.0.0         255.255.255.240 U     50     0        0 tun0
89.246.239.32   0.0.0.0         255.255.255.248 U     50     0        0 tun0
145.253.167.96  0.0.0.0         255.255.255.248 U     50     0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
172.20.50.0     0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.20.100.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.20.110.128  0.0.0.0         255.255.255.192 U     50     0        0 tun0
172.20.120.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.20.150.100  0.0.0.0         255.255.255.255 UH    50     0        0 tun0
172.20.160.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.22.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.23.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.24.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.25.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.26.10.0     0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.26.11.0     0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.26.12.0     0.0.0.0         255.255.255.0   U     50     0        0 tun0
172.26.13.0     0.0.0.0         255.255.255.248 U     50     0        0 tun0
172.27.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.28.0.0      0.0.0.0         255.255.0.0     U     50     0        0 tun0
172.29.81.0     0.0.0.0         255.255.255.128 U     50     0        0 tun0
172.29.81.128   0.0.0.0         255.255.255.224 U     50     0        0 tun0
192.168.18.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.24.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.25.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.27.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.28.0    0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.103.0   0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.105.0   0.0.0.0         255.255.255.0   U     50     0        0 tun0
192.168.106.0   0.0.0.0         255.255.255.0   U     50     0        0 tun0
194.97.107.122  0.0.0.0         255.255.255.255 UH    50     0        0 tun0
195.222.249.56  0.0.0.0         255.255.255.248 U     50     0        0 tun0
195.222.249.88  0.0.0.0         255.255.255.248 U     50     0        0 tun0
195.243.141.112 0.0.0.0         255.255.255.240 U     50     0        0 tun0
212.18.198.200  0.0.0.0         255.255.255.248 U     50     0        0 tun0
212.18.214.80   0.0.0.0         255.255.255.248 U     50     0        0 tun0
212.59.32.96    0.0.0.0         255.255.255.240 U     50     0        0 tun0
212.59.36.184   0.0.0.0         255.255.255.248 U     50     0        0 tun0
212.59.56.80    0.0.0.0         255.255.255.252 U     50     0        0 tun0
212.88.130.196  0.0.0.0         255.255.255.252 U     50     0        0 tun0
212.88.140.156  0.0.0.0         255.255.255.252 U     50     0        0 tun0
212.125.39.128  0.0.0.0         255.255.255.240 U     50     0        0 tun0
212.125.39.152  0.0.0.0         255.255.255.252 U     50     0        0 tun0
212.125.39.192  0.0.0.0         255.255.255.240 U     50     0        0 tun0
212.125.45.64   0.0.0.0         255.255.255.192 U     50     0        0 tun0
213.23.120.128  0.0.0.0         255.255.255.240 U     50     0        0 tun0
217.5.148.184   0.0.0.0         255.255.255.248 U     50     0        0 tun0
217.5.148.208   0.0.0.0         255.255.255.248 U     50     0        0 tun0
217.5.221.208   0.0.0.0         255.255.255.240 U     50     0        0 tun0
217.89.134.56   0.0.0.0         255.255.255.248 U     50     0        0 tun0
217.91.11.112   10.77.96.1      255.255.255.255 UGH   600    0        0 wlp3s0

```

```

cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

```

```

ping -c3 ubuntuforums.com

PING ubuntuforums.com (91.189.94.16) 56(84) bytes of data.
64 bytes from marula.canonical.com (91.189.94.16): icmp_seq=1 ttl=54 time=35.9 ms
64 bytes from marula.canonical.com (91.189.94.16): icmp_seq=2 ttl=54 time=37.3 ms
64 bytes from marula.canonical.com (91.189.94.16): icmp_seq=3 ttl=54 time=37.7 ms

--- ubuntuforums.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 35.963/37.041/37.763/0.792 ms

```

```

ping wiki.mycompany.com

ping: wiki.mycompany.com: Name or service not known

```

---

### Post by palazzo2 on 2017-07-28
Same without VPN:

```

ifconfig

enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:e1:ad:22:d3:56  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf2300000-f2320000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 730  bytes 55762 (55.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 730  bytes 55762 (55.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.77.96.207  netmask 255.255.248.0  broadcast 10.77.103.255
        inet6 fe80::1eec:a89:5f83:b642  prefixlen 64  scopeid 0x20<link>
        ether f8:59:71:31:e5:d4  txqueuelen 1000  (Ethernet)
        RX packets 629145  bytes 623819197 (623.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 218732  bytes 31012482 (31.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.77.96.1      0.0.0.0         UG    600    0        0 wlp3s0
10.77.96.0      0.0.0.0         255.255.248.0   U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

```

---

### Post by cariboo on 2017-07-29
Do you have something like this in your openvpn config file:

```
client
remote 1-ca.xx-xxxxxxx 443
dev tun 
proto udp
auth-user-pass


resolv-retry infinite 
redirect-gateway def1
persist-key
persist=tun
```

make note of the tun device

---

### Post by palazzo2 on 2017-07-30
Which file should I look at? My /etc/openvpn is empty.

---

### Post by cariboo on 2017-07-30
You should have provided with a configuration file from your vpn provider. I downloaded the one from my service provider, and copied it to a directory I created called openvpn.

---

### Post by palazzo2 on 2017-07-30
I have 16.04 in my home, and it connects without any problems without a config file. I provided my login credentials to network manager GUI and it worked :) I happen to think that either it's sth with my network manager configuration or 17.04 in general.

---

