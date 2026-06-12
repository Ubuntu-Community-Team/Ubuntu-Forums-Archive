---
title: "No internet connection but LAN just fine"
date: 2021-08-21
forum: Ubuntu/Debian BASED
---

### Post by townhill on 2021-08-21
My wife is running Zorin 16 on a Lenove Thinkpad E14. She has had no problem with connecting to the internet via wireless until recently.  We have both started using protonvpn on our laptops, which may or may not be relevant.  A couple of days ago she lost internet connection both when logged in to the vpn or with the vpn connection stopped.  It seemed that when her computer went to sleep it lost the vpn connection and when I restarted the vpn on her machine she was able to connect again, also with or without the vpn.  Yesterday she lost all internet connection.  She can connect to the local wireless network without a problem.  Our router shows that she is connected and I can ping her laptop successfully from mine.  She is able to access the Nextcloud server running on our RPI.  But no internet.  I am running Ubuntu 21.04 and am using the proton vpn with no problem.

I thought maybe the problem was the protonvpn "kill switch" which disables an internet connection if the vpn is dropped so I uninstalled it on her machine. I stopped her firewall and confirmed that it is not running.  I thought that the "kill switch' might have done something with the iptables but I am assuming that with the firewall disabled this would not apply.  With the router seeing her machine and her being able to connect to the LAN just fine, I am out of ideas.  I would appreciate some help in figuring this out.  A couple of things I did to check:  

```

Maria@ThinkPad:~$ sudo iwconfig 
[sudo] password for maria:     
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:"Cottagers-5g"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: A8:97:CD:26:9D:4C   
          Bit Rate=650 Mb/s   Tx-Power=23 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0

ipv6leakintrf0  no wireless extensions.

```

and also 

```

maria@ThinkPad:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 8c:8c:aa:64:e4:67
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-27-generic firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:3000(size=256) memory:b1304000-b1304fff memory:b1300000-b1303fff
  *-network
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 00
       serial: 94:08:53:ac:32:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.11.0-27-generic firmware=N/A ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:137 ioport:2000(size=256) memory:b1200000-b120ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: ipv6leakintrf0
       serial: 86:83:ff:f9:12:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dummy driverversion=5.11.0-27-generic

```

i would very much appreciate any help in resolving this problem.

Thanks

---

### Post by wildmanne39 on 2021-08-21
Moved to Other OS Support and Projects as Zorin is not an officially supported Ubuntu flavor.

---

### Post by The Cog on 2021-08-21
More things that might help figure things out - please can you post the output from these commands:
ip address
ip rule
ip route list table all
ip -6 address
ip -6 rule
ip -6 route list table all
cat /etc/resolv.conf
ping -c3 1.1.1.1
ping -c3 one.one.one.one

---

### Post by chili555 on 2021-08-21
I would also like to see:

```
cat /etc/resolv.conf
ls -al /etc/resolv.conf
```

---

### Post by townhill on 2021-08-21
Thanks for the replies, here are the results:  

```
ip address;

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 8c:8c:aa:64:e4:67 brd ff:ff:ff:ff:ff:ff
3: wlp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 94:08:53:ac:32:95 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.13/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp5s0
       valid_lft 3327sec preferred_lft 3327sec
    inet6 2601:601:1101:3070:ff34:2181:3ebe:32fa/64 scope global temporary dynamic 
       valid_lft 3599sec preferred_lft 3599sec
    inet6 2601:601:1101:3070:4b7b:a47e:c5be:5d50/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3599sec preferred_lft 3599sec
    inet6 fe80::a093:9c0d:2c5c:e22c/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: ipv6leakintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 4a:fc:a1:6e:93:9a brd ff:ff:ff:ff:ff:ff
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::8fee:4481:e47e:9369/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

```
ip rule:
  
  0:    from all lookup local
32766:    from all lookup main
32767:    from all lookup default
```

```
ip route list table all:  

default via 192.168.0.1 dev wlp5s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp5s0 scope link metric 1000 
192.168.0.0/24 dev wlp5s0 proto kernel scope link src 192.168.0.13 metric 600 
broadcast 127.0.0.0 dev lo table local proto kernel scope link src 127.0.0.1 
local 127.0.0.0/8 dev lo table local proto kernel scope host src 127.0.0.1 
local 127.0.0.1 dev lo table local proto kernel scope host src 127.0.0.1 
broadcast 127.255.255.255 dev lo table local proto kernel scope link src 127.0.0.1 
broadcast 192.168.0.0 dev wlp5s0 table local proto kernel scope link src 192.168.0.13 
local 192.168.0.13 dev wlp5s0 table local proto kernel scope host src 192.168.0.13 
broadcast 192.168.0.255 dev wlp5s0 table local proto kernel scope link src 192.168.0.13 
::1 dev lo proto kernel metric 256 pref medium
2601:601:1101:3070::/64 dev wlp5s0 proto ra metric 600 pref medium
fdeb:446c:912d:8da::/64 dev ipv6leakintrf0 proto kernel metric 95 pref medium
fe80::/64 dev ipv6leakintrf0 proto kernel metric 95 pref medium
fe80::/64 dev wlp5s0 proto kernel metric 600 pref medium
default via fdeb:446c:912d:8da::1 dev ipv6leakintrf0 proto static metric 95 pref medium
default via fe80::aa97:cdff:fe26:9d4d dev wlp5s0 proto ra metric 600 pref medium
local ::1 dev lo table local proto kernel metric 0 pref medium
local 2601:601:1101:3070:4b7b:a47e:c5be:5d50 dev wlp5s0 table local proto kernel metric 0 pref medium
local 2601:601:1101:3070:ff34:2181:3ebe:32fa dev wlp5s0 table local proto kernel metric 0 pref medium
local fdeb:446c:912d:8da:: dev ipv6leakintrf0 table local proto kernel metric 0 pref medium
local fe80::8fee:4481:e47e:9369 dev ipv6leakintrf0 table local proto kernel metric 0 pref medium
local fe80::a093:9c0d:2c5c:e22c dev wlp5s0 table local proto kernel metric 0 pref medium
multicast ff00::/8 dev ipv6leakintrf0 table local proto kernel metric 256 pref medium
multicast ff00::/8 dev wlp5s0 table local proto kernel metric 256 pref medium
```

```
ip -6 address  

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1000
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
3: wlp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 2601:601:1101:3070:ff34:2181:3ebe:32fa/64 scope global temporary dynamic 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 2601:601:1101:3070:4b7b:a47e:c5be:5d50/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 fe80::a093:9c0d:2c5c:e22c/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: ipv6leakintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 state UNKNOWN qlen 1000
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::8fee:4481:e47e:9369/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

```
ip -6 rule
  
0:    from all lookup local
32766:    from all lookup main
```

```
ip -6 route list table all  

::1 dev lo proto kernel metric 256 pref medium
2601:601:1101:3070::/64 dev wlp5s0 proto ra metric 600 pref medium
fdeb:446c:912d:8da::/64 dev ipv6leakintrf0 proto kernel metric 95 pref medium
fe80::/64 dev ipv6leakintrf0 proto kernel metric 95 pref medium
fe80::/64 dev wlp5s0 proto kernel metric 600 pref medium
default via fdeb:446c:912d:8da::1 dev ipv6leakintrf0 proto static metric 95 pref medium
default via fe80::aa97:cdff:fe26:9d4d dev wlp5s0 proto ra metric 600 pref medium
local ::1 dev lo table local proto kernel metric 0 pref medium
local 2601:601:1101:3070:4b7b:a47e:c5be:5d50 dev wlp5s0 table local proto kernel metric 0 pref medium
local 2601:601:1101:3070:ff34:2181:3ebe:32fa dev wlp5s0 table local proto kernel metric 0 pref medium
local fdeb:446c:912d:8da:: dev ipv6leakintrf0 table local proto kernel metric 0 pref medium
local fe80::8fee:4481:e47e:9369 dev ipv6leakintrf0 table local proto kernel metric 0 pref medium
local fe80::a093:9c0d:2c5c:e22c dev wlp5s0 table local proto kernel metric 0 pref medium
multicast ff00::/8 dev ipv6leakintrf0 table local proto kernel metric 256 pref medium
multicast ff00::/8 dev wlp5s0 table local proto kernel metric 256 pref medium
```

```
cat /etc/resolv.conf

# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad
```

```
ping -c3 1.1.1.1

PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=55 time=23.1 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=55 time=18.5 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=55 time=14.0 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.964/18.522/23.090/3.725 ms
```

```
ping -c3 one.one.one.one

ping: one.one.one.one: Temporary failure in name resolution
```

Hope this helps

---

### Post by chili555 on 2021-08-21
Please:

```
ls -al /etc/resolv.conf
```

---

### Post by townhill on 2021-08-21
Sorry, bad copy/paste

```
ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Apr 24 14:52 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
```

---

### Post by chili555 on 2021-08-21
Looks perfect so far, except...it just doesn't work.

How about: ```
sudo service systemd-resolved status
```

---

### Post by townhill on 2021-08-21
Yup, frustrating

```
systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; ven>
     Active: active (running) since Sat 2021-08-21 17:52:21 PDT; 3min 34s ago
       Docs: man:systemd-resolved.service(8)
             https://www.freedesktop.org/wiki/Software/systemd/resolved
             https://www.freedesktop.org/wiki/Software/systemd/writing-network->
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver>
   Main PID: 440 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 9058)
     Memory: 8.5M
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;440 /lib/systemd/systemd-resolved

Aug 21 17:55:32 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:32 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:37 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:37 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:41 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:41 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:46 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:46 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >
Aug 21 17:55:51 moi-ThinkPad systemd-resolved[440]: Using degraded feature set >

```

---

### Post by The Cog on 2021-08-22
This may help: [https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu](https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu)

---

### Post by townhill on 2021-08-22
Thanks.  I'll look into the systemd-resolved thread and I'll post whatever it is that gets things working again here when it's done.

---

### Post by townhill on 2021-08-22
Ok, it was protonvpn that was the problem.  I had uninstalled it suspecting that the killswitch feature was the culprit but I came across [ewogs post]("https://ubuntuforums.org/showthread.php?t=2465968") on Ubuntu Official Flavors Support - Network & Wireless and that did the trick.  Although I had uninstalled it, it seems there was still some cleanup to do.  I am going to reinstall protonvpn as I really like it and it has been working fine on my Ubuntu machine but at least I know how to fix the problem if it happens again. Thank you for your help and advice and if nothing else I learned a few things :P

---

