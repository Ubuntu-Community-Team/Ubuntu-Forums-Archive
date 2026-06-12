---
title: "[RESOLVED]VirtualBox: Host Windows7 cannot Ping Ubuntu Guess"
date: 2015-11-17
forum: Virtualisation
---

### Post by dangerzonen on 2015-11-17
Hi Team,

I'm dz. first of all thank you for helping me.

I've installed ubuntu server as my guest in windows7 host. everthing works fine except for ping from host to guest.
Problem:My ubuntu guest able to ping my windows7 host but windows 7 host not able to ping my guest ubuntu.
I've search the web and looking for some solutions but still fail to resolve.

I've change from NAT to host only or bridge but still fail and even make my ubuntu cannot ping the host.
I've change /etc/network/interfaces and add manually fix IP (192.168.10.200) and still didn't work..
I've tried add 2 adapter (adapter1 NAT and adapter2 bridge/host only) no luck....still fail to ping my host.

Windows IP 192.168.10.110

I've normalize everything back to default

eth0      Link encap:Ethernet  HWaddr 08:00:27:90:1b:72  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe90:1b72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3149 (3.1 KB)  TX bytes:11828 (11.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7775 (7.7 KB)  TX bytes:7775 (7.7 KB)


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


I'm really dun know what to do. May be I'm doing wrong or even miss some of the steps. I hope somebody could assist me further. Thank you for your time.
Thank you.

Regards,
dz

---

### Post by TheFu on 2015-11-18
Set the VM networking to bridged and reboot the VM. Bridged mode is what you want, not "host-only" or NAT.

Some light reading on the differences:
[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

Based on the data posted above you are not in bridged mode.

---

### Post by dangerzonen on 2015-11-19
Hi TheFu,

Yes...its work..thank you...

1. Set fix static IP network/interface.
2. Set VM to bridge.

Good...

---

