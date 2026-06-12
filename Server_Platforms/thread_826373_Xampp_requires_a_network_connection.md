---
title: "Xampp requires a network connection?"
date: 2008-06-11
forum: Server Platforms
---

### Post by thenetduck on 2008-06-11
hi
I have xampp installed but for some reason it will not run unless there is a network connection. What I mean is, when I start Xampp up, it doesn't give me an error or anything but when I go to localhost it blanks out. After I plug a network connection in, it works perfectly. It doesn't have to be connected to the interent, just connected to a network. 

Has anyone experienced this problem? Does anyone know how to fix this? It seems that it checks to see if there is a network and doesn't patch to the xampp server unless it sees one there. 

Anway, any help is welcome. Thanks

The Net Duck

---

### Post by quelx on 2008-06-11
I think if you explicitly tell apache to bind to the **lo** adapter's address, 127.0.0.1, it should start right up.  eg. in the httpd.conf file look for **Listen 80** and change it to **Listen 127.0.0.1:80**

---

### Post by borahshadow on 2008-06-12
I've noticed this with the default ubuntu LAMP configuration. It does not have to even be a real network. I once plugged my laptop into a hub(or router not sure which one it was an old one I had laying around) and nothing else was plugged into it but kubuntu grabbed an ip and it worked.

---

### Post by thenetduck on 2008-06-14
> **quelx said:**
> I think if you explicitly tell apache to bind to the **lo** adapter's address, 127.0.0.1, it should start right up.  eg. in the httpd.conf file look for **Listen 80** and change it to **Listen 127.0.0.1:80**

Tested this out and it didn't seem to work. Still not start until connected to some how to a network. I tried different variations of localhost 127.0.0.1 etc... 


I wish I could pin point the cause. 

Thanks 
The Net Duck

---

### Post by Dr Small on 2008-06-14
Perhaps your host file is messed up. Look for an entry like:
```
127.0.0.1    localhost
```

Also, try '127.0.0.1' in your browser.

---

### Post by borahshadow on 2008-06-14
Ya that works fine but only if the computer is on a network.

---

### Post by Dr Small on 2008-06-14
That doesn't make sense, as lo is it's own loopback device. That should be working.

What does 'ifconfig -a' produce?

---

### Post by borahshadow on 2008-06-14
eth0      Link encap:Ethernet  HWaddr 00:1d:09:c5:48:84
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:c5:48:84
          inet addr:169.254.6.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:49521073 (47.2 MB)  TX bytes:49521073 (47.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:4d:50:32
          inet addr:192.168.0.83  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe4d:5032/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:69412485 (66.1 MB)  TX bytes:6829104 (6.5 MB)
          Interrupt:20 Memory:c0200000-c0204000
hope that helps. BTW I'm using Kubuntu but that shoulden't matter. I am not using Xampp but installed ubuntu LAMP with tasksel

---

### Post by thenetduck on 2008-06-15
> **Dr Small said:**
> That doesn't make sense, as lo is it's own loopback device. That should be working.

What does 'ifconfig -a' produce?

eth0      Link encap:Ethernet  HWaddr 00:1e:37:cb:48:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1800 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:242212 (236.5 KB)  TX bytes:242212 (236.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:51:12:79  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe51:1279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2141117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2113555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1325261249 (1.2 GB)  TX bytes:420453598 (400.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-51-12-79-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


This is what I got for my machine... running a ThinkPad R Series with wireless ABGN 

The Net Duck

---

### Post by thenetduck on 2008-06-15
I think it has something to do with 

/etc/network/interfaces

Because ... these two posts... 

[http://www.linuxforums.org/forum/ubuntu-help/111276-localhost-does-not-respond-lampp.html](http://www.linuxforums.org/forum/ubuntu-help/111276-localhost-does-not-respond-lampp.html)
[http://www.certforums.co.uk/forums/thread21800.html](http://www.certforums.co.uk/forums/thread21800.html)

I don't know what to modify though....

The Net Duck

---

### Post by borahshadow on 2008-06-30
Hey I figured this out. When no network is connected something must tell firefox to go into offline mode. If you go to File> and uncheck work offline it should work. It worked when I tried it but I only tried it once.

---

