---
title: "Windows7 on vbox with no internet connection"
date: 2013-06-17
forum: Virtualisation
---

### Post by Josie86 on 2013-06-17
Hello,

I've a Windows 7 vbox installation and everything is working fine, except internet connection. I've installed vbox mainly to play online and use Sky go, so I really need internet connection in the virtualized machine.

I've already read of similar problems on various forums but I couldn't get this to work, so I decided to post here.

Basically I've tried every network option available in vbox but the result is always the same: no internet connection and no ethernet driver installed in the vbox.

Here's the result of ifconfig command on my ubuntu host, where internet works flawlessly by cable connection.

```
eth0      Link encap:Ethernet  IndirizzoHW bc:5f:f4:58:87:e6  
          indirizzo inet:10.62.17.111  Bcast:10.62.31.255  Maschera:255.255.240.0
          indirizzo inet6: fe80::be5f:f4ff:fe58:87e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113887 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:151125811 (151.1 MB)  Byte TX:19663332 (19.6 MB)

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7951 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:907057 (907.0 KB)  Byte TX:907057 (907.0 KB)

vmnet1    Link encap:Ethernet  IndirizzoHW 00:50:56:c0:00:01  
          indirizzo inet:172.16.142.1  Bcast:172.16.142.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

vmnet8    Link encap:Ethernet  IndirizzoHW 00:50:56:c0:00:08  
          indirizzo inet:192.168.138.1  Bcast:192.168.138.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

```

---

### Post by dragonfly41 on 2013-06-17
I had similar problems in setting up Ubuntu guest OS to have internet connection .. without Bridged Adapter (since I only had cable connection and no router).  I found this video tutorial helpful ..
[URL="http://http://www.youtube.com/watch?v=Jk5Kfm2-Muk"]
http://www.youtube.com/watch?v=Jk5Kfm2-Muk[/URL]

Perhaps adapt to Windows 7 guest.

...................

[COLOR=#b22222][Later edit]  Just to clarify that Bridged Adapter did not seem to work with direct cable connection with no router (at least for me).   
So I had to use Host-only Adapter and NAT .. in that order as explained in the video.

Adapter 1 PCnet Fast III (Host-only Adapter, 'vboxnet0')
Promiscuous Mode: Deny

Adapter 2 PCnet Fast III (NAT)
Promiscuous Mode: Deny
[/COLOR]

---

### Post by Josie86 on 2013-06-17
> **dragonfly41 said:**
> I had similar problems in setting up Ubuntu guest OS to have internet connection .. without Bridged Adapter (since I only had cable connection and no router).  I found this video tutorial helpful ..
[URL="http://http://www.youtube.com/watch?v=Jk5Kfm2-Muk"]
http://www.youtube.com/watch?v=Jk5Kfm2-Muk[/URL]

Perhaps adapt to Windows 7 guest.

...................

[COLOR=#b22222][Later edit]  Just to clarify that Bridged Adapter did not seem to work with direct cable connection with no router (at least for me).   
So I had to use Host-only Adapter and NAT .. in that order as explained in the video.

Adapter 1 PCnet Fast III (Host-only Adapter, 'vboxnet0')
Promiscuous Mode: Deny

Adapter 2 PCnet Fast III (NAT)
Promiscuous Mode: Deny
[/COLOR]

Hi dragonfly and thanks for your reply.

I've tried with your method but it's not working :-(

---

### Post by dragonfly41 on 2013-06-17
What adapters have you set up in VirtualBox?

---

### Post by Josie86 on 2013-06-17
> **dragonfly41 said:**
> What adapters have you set up in VirtualBox?

The last setup I've tried is the one you suggested 

[COLOR=#b22222]Adapter 1 PCnet Fast III (Host-only Adapter, 'vboxnet0')
Promiscuous Mode: Deny

Adapter 2 PCnet Fast III (NAT)
Promiscuous Mode: Deny
[/COLOR]
But I had already tried pretty much every combination possible ..

---

