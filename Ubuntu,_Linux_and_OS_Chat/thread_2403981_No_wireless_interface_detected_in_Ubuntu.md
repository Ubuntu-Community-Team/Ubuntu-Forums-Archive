---
title: "No wireless interface detected in Ubuntu"
date: 2018-10-18
forum: Ubuntu, Linux and OS Chat
---

### Post by xiajx on 2018-10-18
My Ubuntu on Virtual Machine worked fine until today. The wireless network cannot be detected.  
I downloaded the Intel wireless driver on the Intel website and unzip the zipped file, and then move the .ucode file to /lib/firmware but it still didn't work.
I have checked the system settings -> software and updates -> additional drivers but it says "no additional driver was available".

The result of "ifconfig" is:

root@ubuntu:~# ifconfigeth0      Link encap:Ethernet  HWaddr 00:0c:29:2b:11:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9909 (9.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x2000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:9267 (9.2 KB)  TX bytes:9267 (9.2 KB)

I've also tried lshw -C net and only information about Ethernet Interface was shown, and wireless interface cannot be detected.

root@ubuntu:~# lshw -C net
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:2b:11:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 latency=64 link=no maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:fd500000-fd50ffff

I am offline on Ubuntu so update instructions cannot be executed. Can anybody tell me how my Ubuntu system can connect to the wireless net again?

---

### Post by wildmanne39 on 2018-10-18
Thread closed. Please do not post duplicates, it dilutes community effort.

---

