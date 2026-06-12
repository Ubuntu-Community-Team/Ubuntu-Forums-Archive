---
title: "Internet access problem"
date: 2011-10-09
forum: Server Platforms
---

### Post by LordJebe on 2011-10-09
Firstly, I would like to clarify that the server I have set up is both my first real touch with servers and my first real touch with Ubuntu, so I may have made an awfully noob'ish mistake here. I have read some tutorials and guides but this really is my "first cup of Ubuntu".

Right, so I set up an Ubuntu server just a while ago. I applied a static IP using [this]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") tutorial, and everything seems to work well. I can connect to the server using SSH from another computer in my home network, and I can ping Google without a problem, but I can't download anything. I tried to install curl to check if I can fetch my external IP, and this is what happened:
```
sudo aptitude -y install curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  curl libcurl3{a}
0 packages upgraded, 2 newly installed, 0 to remove and 18 not upgraded.
Need to get 433kB of archives. After unpacking 782kB will be used.
Writing extended state information... Done
Err http://fi.archive.ubuntu.com/ubuntu/ lucid-updates/main libcurl3 7.19.7-1ubuntu1.1
  Temporary failure resolving 'fi.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main libcurl3 7.19.7-1ubuntu1.1
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main curl 7.19.7-1ubuntu1.1
  Temporary failure resolving 'security.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.19.7-1ubuntu1.1_i386.deb: Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
```

With DHCP, I was able to download files normally, but now it's just error, error and a bit more error.

---

### Post by papibe on 2011-10-09
Hi LordJebe. Welcome to the forums!

Could you post the result of these commands?
```
$ sudo lshw -C network

$ lspci -nn | grep -i eth

$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com

$ ps aux | grep -i dhc

```
Please use # tags (available when replying) to paste your results.
Regards.

---

### Post by LordJebe on 2011-10-09
Thanks mate.

sudo lshw -C network
```
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:40:00.0
       logical name: eth0
       version: 01
       serial: 00:14:c2:01:c5:33
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.29a ip=192.168.100.30 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f0400000-f040ffff
```

lspci -nn | grep -i eth
```
40:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:14:c2:01:c5:33
          inet addr:192.168.100.30  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c2ff:fe01:c533/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:86871 (86.8 KB)  TX bytes:109342 (109.3 KB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39352 (39.3 KB)  TX bytes:39352 (39.3 KB)
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    100    0        0 eth0
```


nslookup ubuntu.com
```
;; connection timed out; no servers could be reached
```

dig ubuntu.com
```
; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

ps aux | grep -i dhc
```
root      1057  0.0  0.0   2236   428 ?        Ss   04:55   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
tempest   1882  0.0  0.0   3324   848 pts/1    S+   06:26   0:00 grep --color=auto -i dhc
```

And I just noticed that I can't ping [www.google.com](www.google.com), but I can ping the IP that answered to the ping [www.google.com](www.google.com) command when the connection was fully functioning.

---

### Post by papibe on 2011-10-09
I'm guessing that you didn't restart your machine after changing to a static IP. It looks like the dhcp client is still running.

You can either kill that process, and restart the network, or just restart your machine for a clean install.

Let us know how it goes.
Regards.


EDIT: it would just be simpler to restart your server.

---

### Post by LordJebe on 2011-10-09
Correct, I hadn't restarted my server. Restarted the machine twice, no effect.

ps aux | grep -i dhc
```
tempest    928  0.0  0.0   3324   848 pts/0    S+   06:51   0:00 grep --color=auto -i dhc
```

At least the dhcp client got killed.

---

### Post by papibe on 2011-10-10
Could you post the content of these files?
```
/etc/network/interfaces

/etc/resolv.conf
```
Regards.

---

### Post by LordJebe on 2011-10-10
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.100.30
netmask 255.255.255.0
network 192.268.100.0
broadcast 192.168.100.255
gateway 192.168.100.1
```

/etc/resolv.conf
```
nameserver 192.168.100.30
domain Elisa
search Elisa
```

I have edited both files according to the tutorial I referred to in the first post.

---

### Post by papibe on 2011-10-10
> **LordJebe said:**
> 
```
nameserver **192.168.100.30**
domain Elisa
search Elisa
```

Are you running a DNS server on your own desktop? or did you set dnsmasq?

If not, that line should point to a real DNS. Try your router first:
```
nameserver 192.168.100.1
```
(I'm assuming that that's your router from your routes).

Restart your network:
```
$ sudo service networking restart
```
I try accessing the Internet again.

Regards.

---

### Post by LordJebe on 2011-10-10
Didn't understand the DNS part (I am a sucker at these internet terms and stuff), tried to change the value for nameserver and bingo, it's working. Pinging [www.google.com](www.google.com) works, and nslookup ubuntu.com gives a result. **Thank you** for the help!

---

### Post by papibe on 2011-10-10
:D Glad it's working! Please mark the thread solved when you have the chance.
Regards.

EDIT: Oops, I think you already did.

---

### Post by zandman on 2011-10-18
After being forced to change internal network numbering (192.168.1 changed to 192.168.2) because i got a new router from the ISP: "sudo apt-get update" didn't work.
The pointer to /etc/resolv.conf was the one that helped me fix it.
"nameserver 192.168.1.xxx", when i saw that i immediately knew what to fix.
Changed that, now updates are running as usual.

Thanks.:D

---

