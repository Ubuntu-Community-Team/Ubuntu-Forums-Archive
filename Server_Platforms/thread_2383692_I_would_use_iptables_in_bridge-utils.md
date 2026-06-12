---
title: "I would use iptables in bridge-utils"
date: 2018-01-28
forum: Server Platforms
---

### Post by iacoposk8 on 2018-01-28
Hello everyone, i have a server with eth0 and eth1 and fro create a bridge i did this:
```

sudo apt-get install bridge-utils -y
sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback
 
iface eth0 inet manual
 
iface eth1 inet manual
 
auto br0
iface br0 inet dhcp
  bridge_ports eth0 eth1

```
and all works! but if i want use iptables for block a mac address if i use
```
sudo ebtables -A FORWARD -s 20:cf:30:3e:68:2a -j DROP
```
works, but if i use:
```
sudo iptables -A FORWARD -m mac --mac-source 20:cf:30:3e:68:2a -j DROP
```
doesn't work, i preffer do it with iptables because i need the --timestart option and there is only in iptables
thanks

---

### Post by Doug S on 2018-01-28
Well, you seem to be correct, it doesn't work. Works fine on the INPUT chain. I don't know about your case, but in my test case the packets, destined via my br0 for a VM guest, don't even traverse the iptables rule set, and so wouldn't be caught by any rule. I would have to filter them on the INPUT chain in the VM itself.

---

### Post by iacoposk8 on 2018-01-29
thanks for the answer :)
I used this:
```
sudo iptables -A INPUT -m mac --mac-source 20:cf:30:3e:68:2a -j DROP
```
Now i can't connect via ssh, but I can do, ping, speedtest etc.
there is a way for debug and try to understand where is the problem?
thanks

---

### Post by Doug S on 2018-01-29
> **iacoposk8 said:**
> thanks for the answer :)
I used this:
```
sudo iptables -A INPUT -m mac --mac-source 20:cf:30:3e:68:2a -j DROP
```
Now i can't connect via ssh, but I can do, ping, speedtest etc.
there is a way for debug and try to understand where is the problem?
thanksWell, I would do two things:

first, add a logging rule:
```
sudo iptables -A INPUT -m mac --mac-source 20:cf:30:3e:68:2a -j LOG --log-prefix "MAC BLOCK:" --log-level info
sudo iptables -A INPUT -m mac --mac-source 20:cf:30:3e:68:2a -j DROP
```

Second, use tcpdump to observe what is going on at the packet level.

Otherwise we will have to have more information about your exact setup and what you are doing.

---

### Post by iacoposk8 on 2018-01-30
thanks for the answer, this is the part of result
```

19:31:19.772473 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.773824 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.774151 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.775349 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 120
19:31:19.776143 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.777489 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.777640 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.778790 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.779143 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.780306 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.823572 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.824692 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.825056 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.825961 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.826749 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.827645 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.828244 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.829116 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.829948 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.830833 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.843770 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.844647 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.892220 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.893262 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.893887 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.894806 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.897381 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.898261 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.912379 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.913263 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.913885 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:19.914749 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:19.999270 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.000280 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:20.099711 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.101200 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.102449 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:20.346046 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.390976 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:20.424767 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.500533 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.501775 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104
19:31:20.502009 IP 89.46.222.45.openvpn > 192.168.1.103.37433: UDP, length 1381
19:31:20.571481 IP 192.168.1.103.37433 > 89.46.222.45.openvpn: UDP, length 104

```

---

### Post by iacoposk8 on 2018-02-05
up:)

---

### Post by Doug S on 2018-02-06
> **iacoposk8 said:**
> up:)Well, there wasn't any useful information in your tcpdump capture, so I was waiting for more. The log entries would be useful.

---

