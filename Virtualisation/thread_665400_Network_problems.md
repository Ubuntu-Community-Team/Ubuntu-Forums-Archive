---
title: "Network problems"
date: 2008-01-12
forum: Virtualisation
---

### Post by babinos on 2008-01-12
I successfully installed ubuntu 7.10 on vmware fusion. Network was ok and i did all the available updates. Installed vmware tools and when i rebooted i had no network!

When i click on the network icon it says "No network devices have been found".

This is what i get from ifconfig:

eth0 Link encap:Ethernet HWaddr 00:0C:29:ED:F5:2D 
inet addr:172.16.77.128 Bcast:172.16.77.255 Mask:255.255.255.0
inet6 addr: fe80::20c:29ff:feed:f52d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:83 errors:81 dropped:0 overruns:0 frame:0
TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:26967 (26.3 KB) TX bytes:34303 (33.4 KB)
Interrupt:16 Base address:0x2024 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:73 errors:0 dropped:0 overruns:0 frame:0
TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:17070 (16.6 KB) TX bytes:17070 (16.6 KB)

Can anyone help me out, please?

---

### Post by fjgaude on 2008-01-12
Are you using NAT? Do you go through a router?

Your IP may be out of range for your router settings.

---

### Post by babinos on 2008-01-12
Are you using NAT? Do you go through a router?

Your IP may be out of range for your router settings.

Yes, i'm using NAT. I'm on a LAN. I have used both dhcp and manual configuration. The IP i provide is totally correct.

What confuses me is that after installation it was fine! And when the updates were finished i had no network...

 Is there anything else usefull I can post?

---

### Post by fjgaude on 2008-01-12
When you say "updates" you mean Ubuntu updates? If so, you have to re-install VMware by using the .pl script. Understand?

---

### Post by babinos on 2008-01-12
Yes, the ubuntu updates. I've just reinstalled vmware tools and network is still down.

---

### Post by fjgaude on 2008-01-12
It not just the tools but the entire VMware Server that has to be re-installed, or updated to reflect the Ubuntu updates, upgrades.

---

