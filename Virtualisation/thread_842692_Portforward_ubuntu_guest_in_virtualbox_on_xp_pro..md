---
title: "Portforward ubuntu guest in virtualbox on xp pro."
date: 2008-06-27
forum: Virtualisation
---

### Post by markola on 2008-06-27
Hello All,

Trying to setup a static ip in Ubuntu in virtualbox running on xp. I've got Ubuntu running great with guest additions and all. Now I want to get Transmission running at full steam, but can't set up a static ip... I've got this:-

eth0      Link encap:Ethernet  HWaddr 08:00:27:cc:6f:5c  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fecc:6f5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5096256 (4.8 MB)  TX bytes:417811 (408.0 KB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35466 (34.6 KB)  TX bytes:35466 (34.6 KB)

but I've no idea what info to use in order to set-up my static ip; I've tried all the various numbers in various boxes but getting nowhere.

Any ideas? Please.

---

### Post by markola on 2008-06-30
I seem to have found my own answer, a little out-dated maybe but should supply the perfect set-up. So just in case someone else is having similar prob's here's the link...

[http://ubuntuforums.org/showthread.php?t=727503]("http://ubuntuforums.org/showthread.php?t=727503")

---

