---
title: "change subnet IP for XP guest, Vmware server 2.0.1"
date: 2009-07-14
forum: Virtualisation
---

### Post by IQRules on 2009-07-14
The Ubuntu 8.10 server IP is 192.168.1.90.

eth0      Link encap:Ethernet  HWaddr 00:12:79:de:68:65  
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:79ff:fede:6865/64 Scope:Link

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.147.1  Bcast:172.16.147.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link

I do not have vmnet0 here.

The XP guest IP is 172.16.147.128

How to change the XP IP to 192.168.1.x subnet?

My network adapter is in NAT mode, is it correct?

---

### Post by IQRules on 2009-07-14
I kind of fix the issue here.

This is a laptop with wireless wlan0 connection.
I killed the bridge on eth0 nic card. 
To enable bridge on wlan0, I did this. 

# /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-1.pid -n 0 -i wlan0

And from XP guest, I use "bridge" mode.
Now the XP IP is 192.168.1.130 now.
Is there a way to set this up properly for wlan0 instead of manually run this?

---

