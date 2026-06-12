---
title: "Wifi won't reconnect after resuming from sleep."
date: 2014-07-20
forum: System76 Support
---

### Post by vroom2 on 2014-07-20
Hey all!

I just got my System76 Galago Ultrapro on Friday with the free wireless upgrade to the Intel Dual Band Wireless-AC 7260. The problem I'm having with this wireless card is that it'll show a list of networks, but it won't reconnect to the network (or to any network) when I resume from putting the laptop to sleep. It just shows that it's "connecting", and will eventually time out. In order to recover, I need to do a full system restart, which really seems to take the point out of being able to shut the laptop at a moment's notice.

Anyway, here's some information:

**ifconfig before suspend:**```
eth0      Link encap:Ethernet  HWaddr 80:fa:5b:03:f0:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7e00000-f7e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12726 (12.7 KB)  TX bytes:12726 (12.7 KB)

wlan0     Link encap:Ethernet  HWaddr a0:a8:cd:67:88:38  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a2a8:cdff:fe67:8838/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66362 (66.3 KB)  TX bytes:43380 (43.3 KB)



```**Ifconfig after resuming:**```

eth0      Link encap:Ethernet  HWaddr 80:fa:5b:03:f0:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7e00000-f7e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55758 (55.7 KB)  TX bytes:55758 (55.7 KB)

wlan0     Link encap:Ethernet  HWaddr a0:a8:cd:67:88:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

I can provide more information, such as the massively huge dmesg at request.

Any help would be greatly appreciated! I've already sent a support request in to System76, but if anyone else has had this issue, I would be greatful if you would share how you fixed it. Thank you!

---

### Post by varunendra on 2014-07-20
Welcome to the forums vroom2!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by isantop on 2014-07-21
Which version of Ubuntu do you currently have installed? Are you fully up to date?

---

### Post by vroom2 on 2014-07-21
Thanks guys for the help, but it seems that installing wicd somehow fixed it. (I'm at a loss to explain how...)

Thank you!

---

