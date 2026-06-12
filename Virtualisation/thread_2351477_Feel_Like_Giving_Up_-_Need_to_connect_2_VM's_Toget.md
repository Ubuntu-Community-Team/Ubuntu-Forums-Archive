---
title: "Feel Like Giving Up - Need to connect 2 VM's Together"
date: 2017-02-03
forum: Virtualisation
---

### Post by zman593 on 2017-02-03
Okay, i legit feel like giving up. I know its my first post here but ive searched way to many guides.

I have a Windows 10 as host and two VM's in VirtualBox. One running Ubuntu 16.04 Desktop and the other running Windows 10. 

My goal is to connect the Windows 10 VM to Ubuntu 16.04 so that all data from Windows 10 VM goes through the Ubuntu 16.04 VM. My Ubuntu 16.04 VM has 2 adaptors set, one that is Bridged and one in an Internal Network. The Windows 10 VM has only one adaptor, connected to the Internal network.

I cannot, for the life of me, get them to see each other. Ive done everything from setting a manual IP for both and tried to get W10 to connect to it to letting DHCP try to find each other to using the "Share connection" option in Ubuntu. Absolutely nothing works.

I was hoping someone can either show me a full guide or hop on TeamViewer and help me set this up (or maybe get in a Skype call) or something. This is driving me insane as I spent 1 week trying to make it work.

What am i doing wrong?

---

### Post by howefield on 2017-02-03
Thread moved to the "*Virtualisation*" forum.

---

### Post by ODTech on 2017-02-04
> **zman593 said:**
> Okay, i legit feel like giving up. I know its my first post here but ive searched way to many guides.

I have a Windows 10 as host and two VM's in VirtualBox. One running Ubuntu 16.04 Desktop and the other running Windows 10. 

My goal is to connect the Windows 10 VM to Ubuntu 16.04 so that all data from Windows 10 VM goes through the Ubuntu 16.04 VM. My Ubuntu 16.04 VM has 2 adaptors set, one that is Bridged and one in an Internal Network. The Windows 10 VM has only one adaptor, connected to the Internal network.

I cannot, for the life of me, get them to see each other. Ive done everything from setting a manual IP for both and tried to get W10 to connect to it to letting DHCP try to find each other to using the "Share connection" option in Ubuntu. Absolutely nothing works.

I was hoping someone can either show me a full guide or hop on TeamViewer and help me set this up (or maybe get in a Skype call) or something. This is driving me insane as I spent 1 week trying to make it work.

What am i doing wrong?

Tell us the reason for your goal, it will help us understand and guide you better. 

Is the Ubuntu VM a firewall and you will eventualy end up doing all your work on the Windows 10 VM? 
Is Ubuntu going to be a fileserver?
Probably a silly question but have you installed Samba on ubuntu?

---

### Post by efflandt on 2017-02-04
By default virtualbox sets up each network connection on each guest doing NAT through the IP of the host. So if you wanted to route the Win10 guest through Ubuntu guest, you would need to configure all of the guest network connections as bridged. Configure the Win10 guest network and and one of the Ubuntu guest networks as different static IP addresses and netmask in same network that is a different network from real LAN. Give Win10 guest default gateway to Ubuntu guest in that network. If you want the Win10 guest to be able to access main LAN or Internet, Ubuntu guest would need to be configured to do routing and possibly firewall or iptables rules to masquerade and possibly log network activity of the Win10 guest. To verify if routing is enabled in Ubuntu for ipv4 **cat /proc/sys/net/ipv4/ip_forward** should return 1, but I am not sure how to verify that with any config for ipv6.

Actually the network on Ubuntu guest to real LAN does not necessarily need to be bridged unless you need to initiate a connection from Win10 "host" or real LAN to Ubuntu. The default NAT would masquerade Ubuntu guest's IP as the IP of the host if you only need to access real LAN and beyond from Ubuntu guest, but do not need to access Ubuntu guest from real LAN connection or host.

PS: This is an example of 2 virtual hosts configured with bridged connections able to see each other (but not one configured to route through the other). Note that for them to see each other with .local domain, they need to be configured with **publish-workstation=yes** in **/etc/avahi/avahi-daemon.conf** (for this demo, although, with Windows to access by name instead of IP would need to do something with samba in Linux):```
From vb1606-32 guest on msata512-1610 host:

efflandt@vb1604-32:~$ avahi-browse -alt
+ enp0s3 IPv6 SSH Remote Terminal                           SSH Remote Terminal  local
+ enp0s3 IPv4 SSH Remote Terminal                           SSH Remote Terminal  local
+ enp0s3 IPv6 D3495208D349                                  iPod Touch Music Library local
+ enp0s3 IPv4 D3495208D349                                  iPod Touch Music Library local
+ enp0s3 IPv6 msata512-1610 [78:e4:00:26:b8:ac]             Workstation          local
+ enp0s3 IPv6 vb1404-64 [08:00:27:5a:02:b3]                 Workstation          local
+ enp0s3 IPv4 msata512-1610 [78:e4:00:26:b8:ac]             Workstation          local
+ enp0s3 IPv4 vb1404-64 [08:00:27:5a:02:b3]                 Workstation          local

efflandt@vb1604-32:~$ ping -c1 vb1404-64.local
PING vb1404-64.local (172.16.0.148) 56(84) bytes of data.
64 bytes from 172.16.0.148: icmp_seq=1 ttl=64 time=0.667 ms

--- vb1404-64.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.667/0.667/0.667/0.000 ms


From vb1404-64 guest on msata512-1610 host:

efflandt@vb1404-64:~$ avahi-browse -alt
+   eth0 IPv6 D3495208D349                                  iPod Touch Music Library local
+   eth0 IPv4 D3495208D349                                  iPod Touch Music Library local
+   eth0 IPv6 SSH Remote Terminal                           SSH Remote Terminal  local
+   eth0 IPv4 SSH Remote Terminal                           SSH Remote Terminal  local
+   eth0 IPv6 vb1604-32 [08:00:27:5a:02:b3]                 Workstation          local
+   eth0 IPv6 msata512-1610 [78:e4:00:26:b8:ac]             Workstation          local
+   eth0 IPv4 vb1604-32 [08:00:27:5a:02:b3]                 Workstation          local
+   eth0 IPv4 msata512-1610 [78:e4:00:26:b8:ac]             Workstation          local

efflandt@vb1404-64:~$ ping -c1 vb1604-32.local
PING vb1604-32.local (172.16.0.145) 56(84) bytes of data.
64 bytes from 172.16.0.145: icmp_seq=1 ttl=64 time=1.98 ms

--- vb1604-32.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.985/1.985/1.985/0.000 ms
```

---

### Post by zman593 on 2017-02-04
I have two VM's. One with Windows 10 and one with Ubuntu 16.04 Desktop LTS VM.

The goal is that everything in the Windows 10 VM has to pass through the Ubuntu 16.04 VM as I plan to do testing on the Windows 10 VM and proxy the traffic via Ubuntu VM.
[B]The big thing is that the windows vm HAS to be in an internal network, not bridged. Since im testing malware, malware may play with my connection settings thus exposing my IP. If i force the Windows 10 VM in an Internal network, if it tries to change connection settings (like IP and DNS), it will be cut off which will alert me its trying to change something

[/B]Anyway, I have Webmin and BIND9 installed on Ubuntu and I set static IP's for both:
[LIST]
[*]Ubuntu Internal IP: 192.168.0.1
[*]Windows Internal IP: 192.168.0.2
[/LIST]
I also have the Windows VM connected:
[IMG]http://i.imgur.com/vawTJ4K.png[/IMG]

I can successfully ping the Ubuntu VM from Windows and Vice Versa so I know they can see each other on the internal network

My only problem is making the Windows VM actually connect to the Ubuntu VM's internet. 

The only option I did in Webmin is this:
[IMG]http://i.imgur.com/QzKsZAt.png[/IMG]

How would I set up so my Windows 10 VM will now connect?

---

### Post by howefield on 2017-02-04
Threads merged.

---

### Post by efflandt on 2017-02-08
I guess I had not paid attention to the types of networks in virtualbox and had not noticed the "internal" network. I did that and can ping between vhosts on internal network. I have done masquerading through Linux, even through an IP and alias IP on the same nic, and bind9 as caching nameserver with zone for my LAN, but that was a long time ago and I have not used webmin.

I did use ufw based on [https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html) to configure masquerade on one vhost and was able to ping through it from other vhost```
efflandt@vb1404-64:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

efflandt@vb1404-64:~$ ping -c1 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.540 ms

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.540/0.540/0.540/0.000 ms

Other vhost's bridged IP (real LAN IP):
efflandt@vb1404-64:~$ ping -c1 172.16.0.145
PING 172.16.0.145 (172.16.0.145) 56(84) bytes of data.
64 bytes from 172.16.0.145: icmp_seq=1 ttl=64 time=0.443 ms

--- 172.16.0.145 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.443/0.443/0.443/0.000 ms

DSL gateway:
efflandt@vb1404-64:~$ ping -c1 172.16.0.254
PING 172.16.0.254 (172.16.0.254) 56(84) bytes of data.
64 bytes from 172.16.0.254: icmp_seq=1 ttl=63 time=1.96 ms

--- 172.16.0.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.960/1.960/1.960/0.000 ms

Internet:
efflandt@vb1404-64:~$ ping -c1 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=20.9 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 20.987/20.987/20.987/0.000 ms
```

---

