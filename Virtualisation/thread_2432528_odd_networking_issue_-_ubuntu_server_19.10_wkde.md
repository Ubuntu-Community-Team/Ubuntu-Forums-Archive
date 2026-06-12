---
title: "odd networking issue - ubuntu server 19.10 w/kde"
date: 2019-12-04
forum: Virtualisation
---

### Post by carlo-1973 on 2019-12-04
I'm having a really really odd issue.
s
I'm running Ubuntu Server 19.10 on a virtual box.  From terminal I am able to access the internet without issues
I later installed KDE on the server (its been a few years since I have worked in linux and I'm trying to get my feet wet again). 
After KDE installed - I noticed that KDE itself did not seem to have access to the internet, however I was able to surf via Firefox, and I was able to ping out and connect to resources via terminal.  Today there was some sort of update or something occured, and now I am unable to connect to resources from within Firefox and other apps in KDE - however I am still able to access all network resources via terminal - even when launched from within KDE. 
I have tried to configure networking in the KDE  within the KDE plasma network app - but still it isn't working within KDE.


Hopefully I can get some assistance to get this fixed up. 

Below is excerpts of the network information. 
I tried to attach screenshots but I'm not sure if they attached properly.
And yes - I am trying to use enp0s5 interface name
Thanks in advance



$netstat -i
Kernel Interface table
Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
enp0s3    1500 78388459      0      0 0      46887006      0      0      0 BMRU
lo       65536    67952      0      0 0         67952      0      0      0 LRU
tun0      1500 77990407      0      0 0      46863319      0 145041      0 MOPRU



$ping [www.google.com]("http://www.google.com")

PING [www.google.com]("http://www.google.com") (172.217.17.68) 56(84) bytes of data.
64 bytes from ams16s30-in-f4.1e100.net (172.217.17.68): icmp_seq=1 ttl=57 time=136 ms
64 bytes from ams16s30-in-f4.1e100.net (172.217.17.68): icmp_seq=2 ttl=57 time=136 ms
64 bytes from ams16s30-in-f4.1e100.net (172.217.17.68): icmp_seq=4 ttl=57 time=141 ms
64 bytes from ams16s30-in-f4.1e100.net (172.217.17.68): icmp_seq=5 ttl=57 time=147 ms
64 bytes from ams16s30-in-f4.1e100.net (172.217.17.68): icmp_seq=6 ttl=57 time=134 ms
^C
--- [www.google.com]("http://www.google.com") ping statistics ---
6 packets transmitted, 5 received, 16.6667% packet loss, time 5019ms
rtt min/avg/max/mdev = 133.908/138.707/146.618/4.656 ms


$ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:54:77:dd brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 63760sec preferred_lft 63760sec
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.57.0.94 peer 10.57.0.93/32 scope global tun0
       valid_lft forever preferred_lft forever

---

### Post by wildmanne39 on 2019-12-04
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-12-04
Are you using NAT or bridged networking in the VM?  Bridged might be the better choice since it puts the VM directly on the local network. It will then get its IP configuration from the router using DHCP.  In general, bridged networking makes more sense for servers since you want the other machines on the network to be able to communicate with the VM. Using NAT hides the VM behind the host.

---

### Post by carlo-1973 on 2019-12-04
I will try that tonight. Being a test environment I was trying to keep it segregated from the rest of my network so I used NAT, but for the sake of testing purposes I will try bridged and see if things work properly. I just find it really weird that it works fine within terminal (even when the terminal is an app within KDE), but the software store and the network connection settings app refused to communicate.  Usually if there is a network issue, it affects all network applications regardless if its in terminal or not.

---

