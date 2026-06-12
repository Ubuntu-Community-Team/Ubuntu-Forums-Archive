---
title: "Wireless Works, Wired Doesn't - Starling Netbook"
date: 2010-07-23
forum: System76 Support
---

### Post by vttay03 on 2010-07-23
--Well the subject says it all.  I don't have any problems connecting to a wireless network with my Starling, but when I plug an ethernet cable in, it just sits there and tries to acquire an IP for a minute or so before timing out.  This seems to be the opposite issue of what most people see; most people have wireless issues but their wired connection works fine.  Any thoughts?  I will say the last time I remember it working I setup an ad-hoc network to share the internet connection since the hotel we were staying in didn't have wireless.  But I don't recall having any issues....any insight is appreciated.

Output of ifconfig -a is below:

```


eth0      Link encap:Ethernet  HWaddr 00:26:9e:01:44:aa  
          inet6 addr: fe80::226:9eff:fe01:44aa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:26 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936 (1.9 KB)  TX bytes:1936 (1.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:17:c4:91:ba:94  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe91:ba94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by vttay03 on 2010-07-24
Nevermind...I was having a tremendous brain fart and was plugging the wrong end of the ethernet cable into my Starling!  I think it was the result of an extremely long day in which the last thing I felt like doing was figuring out why the wired connection wouldn't work.  I apologize for the premature post...

---

### Post by jdb on 2010-07-24
> **vttay03 said:**
> Nevermind...I was having a tremendous brain fart and was plugging the wrong end of the ethernet cable into my Starling!  I think it was the result of an extremely long day in which the last thing I felt like doing was figuring out why the wired connection wouldn't work.  I apologize for the premature post...

LOL, been there, done that

jdb

---

