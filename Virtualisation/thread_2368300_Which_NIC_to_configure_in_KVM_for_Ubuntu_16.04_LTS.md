---
title: "Which NIC to configure in KVM for Ubuntu 16.04 LTS that eth0 comes up again?"
date: 2017-08-09
forum: Virtualisation
---

### Post by dirk-lehmann on 2017-08-09
Hello,

I exported one of my virtual maschines from Oracle virtualbox to ova 2.0 and converted this file to KVM qcow2 like described for example in this tutorial:

[https://utappia.org/2016/04/20/how-to-migrate-virtual-box-machines-to-](https://utappia.org/2016/04/20/how-to-migrate-virtual-box-machines-to-)[the-kvm-virtmanager/]("https://utappia.org/2016/04/20/how-to-migrate-virtual-box-machines-to-the-kvm-virtmanager/")

Unfortunatly this vm does not bring up eth0 when started by KVM.

Any hint how to fix to get migrated to KVM with DRBD and pacemaker HA?

Best regards,

Dirk
[INDENT=2]Hi Dirk,
 
this is most likely caused by a NIC model not supported by the guest OS'
drivers,  but this is also totally off-topic redarding this is the DRBD ML. I  suggest you consult the KVM/qemu/libvirt MLs on this topic instead.
 
Beste Gruesze,
// Veit
[/INDENT]

---

### Post by efflandt on 2017-08-09
I am not familiar with KVM, but does a nic show up in output of **ifconfig**? 16.04 and newer no longer call it "eth0". It is called something else based on PCI device numbers (this is in virtualbox):```
~$ ifconfig
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:5a:02:b3  
          inet addr:172.16.0.145  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::af77:4c1e:6164:5aab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4667 (4.6 KB)  TX bytes:9967 (9.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2781 (2.7 KB)  TX bytes:2781 (2.7 KB)

~$ lspci | grep Ethernet
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```In this case it is actually bridged to a WiFi device wlp4s0 on the host (no longer called wlan0).

---

