---
title: "Unable to access port on ubuntu running on VM (Virtualbox)"
date: 2017-06-02
forum: Virtualisation
---

### Post by nickos2 on 2017-06-02
Dear all,

I tried for multiple days and can't get further. I simply try to access my webserver on my linux (Ubuntu 16.04) running on virtualbox. When I curl my port with 'localhost:9200' i receive the answer. So my api is running fine. 

My settings: The firewall is disabled.

Try 1:
adapter 1: Bridged Adapter
adapter 2: Host-only Adapter

Here I can connect with putty on SSH to 172.20.10.12. But unable to connect 172.20.10.12:9200

 ifconfig
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:05:7a:bc
          inet addr:172.20.10.12  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::a00:27ff:fe05:7abc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7428 (7.4 KB)  TX bytes:8081 (8.0 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:174890 (174.8 KB)  TX bytes:174890 (174.8 KB)



Try 2:
Adapter 1: NAT
Adapter 2: Host-only adapter

Unable to connect vi SSH, no pinging.

ifconfig:
emp0s3 inet addr 10.0.2.15

lo Link encap: Local Loopback



Can anyone suggest what settings I need to set? I don't have a specific requirements, but I want to build a VM that locally accessible from the host (windows) and install some program on the ubuntu VM, nothing fancy.
Thank you very much for any suggestion

---

### Post by siben17 on 2017-06-11
In VirtualBox set "Bridged networking" for the interface. You have to configure the interface in the VM operating system.

---

### Post by howefield on 2017-06-11
Thread moved to the "*Unable to access port on ubuntu running on VM (Virtualbox)*" forum.

---

