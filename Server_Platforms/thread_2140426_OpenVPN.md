---
title: "OpenVPN"
date: 2013-04-29
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-04-29
Hello, how does one run an OpenVPN connection in the background and not have it stop when I close the session? 
Thanks

---

### Post by AmbiguousOutlier on 2013-04-29
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.8.0.73       128.0.0.0       UG    0      0        0 tun1
default         10.10.0.57      128.0.0.0       UG    0      0        0 tun0
default         Livebox-AFB0    0.0.0.0         UG    100    0        0 eth0
10.8.0.1        10.8.0.73       255.255.255.255 UGH   0      0        0 tun1
10.8.0.73       *               255.255.255.255 UH    0      0        0 tun1
10.10.0.1       10.10.0.57      255.255.255.255 UGH   0      0        0 tun0
10.10.0.57      *               255.255.255.255 UH    0      0        0 tun0
lh19699.voxilit Livebox-AFB0    255.255.255.255 UGH   0      0        0 eth0
lh19659.voxilit Livebox-AFB0    255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.8.0.73       128.0.0.0       UG    0      0        0 tun1
128.0.0.0       10.10.0.57      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

Have I got multiple openvpns running at the same time? I think I've somehow got some into the background. I need a way to set up a connection and then bring them to the bg and fg so I close it properly. 

Should I be doing this in a bash script?



EDIT: Trial and error has led me to;

screen sudo openvpn server.conf

However, I still think my route output is looking too messy. It's now looking like this;

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.10.0.21      128.0.0.0       UG    0      0        0 tun3
default         10.10.0.57      128.0.0.0       UG    0      0        0 tun2
default         10.8.0.17       128.0.0.0       UG    0      0        0 tun0
default         Livebox-AFB0    0.0.0.0         UG    100    0        0 eth0
10.8.0.1        10.8.0.17       255.255.255.255 UGH   0      0        0 tun0
10.8.0.1        10.8.0.73       255.255.255.255 UGH   0      0        0 tun1
10.8.0.17       *               255.255.255.255 UH    0      0        0 tun0
10.8.0.73       *               255.255.255.255 UH    0      0        0 tun1
10.10.0.1       10.10.0.21      255.255.255.255 UGH   0      0        0 tun3
10.10.0.1       10.10.0.57      255.255.255.255 UGH   0      0        0 tun2
10.10.0.21      *               255.255.255.255 UH    0      0        0 tun3
10.10.0.57      *               255.255.255.255 UH    0      0        0 tun2
lh19699.voxilit Livebox-AFB0    255.255.255.255 UGH   0      0        0 eth0
lh19659.voxilit Livebox-AFB0    255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.10.0.21      128.0.0.0       UG    0      0        0 tun3
128.0.0.0       10.10.0.57      128.0.0.0       UG    0      0        0 tun2
128.0.0.0       10.8.0.17       128.0.0.0       UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

---

