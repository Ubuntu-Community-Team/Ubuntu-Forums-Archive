---
title: "LVM read slowdown during torrent uploads"
date: 2011-07-14
forum: Server Platforms
---

### Post by ross104 on 2011-07-14
Hello! I've made a simple headless home server based on:
1. Motherboard Asus AT4NM10-I (Intel NM10, PCI)
2. CPU integrated Intel Atom D410
3. 2 Gb of RAM
4. Network Card D-Link DGE-528T 10/100/1000 Mbit/s
5. OS Ubuntu Server 10.04.2 (All installed packages are up to date)

Storage build under LVM based on:
1. Samsung HD103SI - 1 Tb, 5400/32 Mb.
2. Hitachi SATA 2000Gb Deskstar 7K3000 - 2 Tb, 7200/64 Mb.

So found one issue:
When torrent upload speed reaches peak speed (160-200 Kbytes/s) huge read slowdown happens. Server becomes almost unreachable... It allows to connect via putty but it takes a lot of time.

Tested top stats during those lags (Deluge, Transmission) - 10-15% CPU usage.

So I think the problem is in LVM and not in CPU.

How is it possible to find weak place in system to avoid those lags... Cause if torrent is seeding it's impossible to watch movies through network form that server.

---

### Post by ross104 on 2011-07-15
Bump

---

### Post by ross104 on 2011-07-18
Bummpp

---

### Post by Entilza on 2011-07-18
What about some io statistics during that time,

what's the %wa figure on top during this time.

Did you install iotop?

When you are accessing the server during this time you sure it's going locally, check your routes.

Also whats the mem% of the torrents during this time how much mem is it using?

---

### Post by psusi on 2011-07-18
Yea, it sounds like you are trying to connect to your server via a completely saturated dsl/cable modem.

This is a network problem, not anything to do with LVM.

---

### Post by ross104 on 2011-07-19
I'm connecting 100% locally on local IP address 10.0.0.200.
Network is based on Gigabit switch with full cooper wires, so I don't think that it causes some troubles.

iotop is installed and during lags I get strange things: 
Total DISK READ: [COLOR="Red"]123.12 K/s[/COLOR] | Total DISK WRITE: 34.63 K/s
marked red section is jumping from 0 to some 100-300 K/s.
stats show that deluge and samba are reading from disk. But they jump too...

Update 1
Made video of peak moment. Connected remotely via internet. Locally video will be few hours later...
YouTube [http://www.youtube.com/watch?v=FTYwZRjEVag](http://www.youtube.com/watch?v=FTYwZRjEVag)
Megaupload [http://www.megaupload.com/?d=6JXH40PT](http://www.megaupload.com/?d=6JXH40PT)

---

### Post by Entilza on 2011-07-19
Those numbers aren't high because it's Kilobytes/second for a HD that's nothing.

Can you show outpt of ethtool eth0  (or whatever device)

Also ifconfig eth0

Try copying a file locally through samba from the ubuntu server  and see what speeds you are getting.  Try both ways..  Watch iotop then and note the difference in speed.

Try pinging the machine during the lag time and see results.

You gotta really narrow it down to network or HD... 

PS. Nice video, lol

---

### Post by ross104 on 2011-07-19
```
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Half 1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

```

eth1      Link encap:Ethernet  HWaddr --:--:--:--:--:--
          inet addr:10.0.0.200  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: ----::----:----:----:----/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30056681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33647315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21054846799 (21.0 GB)  TX bytes:27027320027 (27.0 GB)
          Interrupt:17 Base address:0x6c00

```

Ping during lags (green - torrent paused, red - peak speed seeding):
```

Pinging 10.0.0.200 with 32 bytes of data:
[COLOR="red"]Reply from 10.0.0.200: bytes=32 time=756ms TTL=64
Reply from 10.0.0.200: bytes=32 time=617ms TTL=64
Reply from 10.0.0.200: bytes=32 time=40ms TTL=64[/COLOR]
[COLOR="YellowGreen"]Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64
Reply from 10.0.0.200: bytes=32 time<1ms TTL=64[/COLOR]
[COLOR="Red"]Reply from 10.0.0.200: bytes=32 time=897ms TTL=64
Reply from 10.0.0.200: bytes=32 time=653ms TTL=64
Reply from 10.0.0.200: bytes=32 time=62ms TTL=64[/COLOR]

```

Copying 35Gb file from|to server:
1. From server
[[IMG]http://img195.imageshack.us/img195/9063/downjv.th.png[/IMG]](http://imageshack.us/photo/my-images/195/downjv.png/)
2. On server
[[IMG]http://img838.imageshack.us/img838/6024/up2c.th.png[/IMG]](http://imageshack.us/photo/my-images/838/up2c.png/)
[[IMG]http://img687.imageshack.us/img687/9867/14702560.th.png[/IMG]](http://imageshack.us/photo/my-images/687/14702560.png/)


Strange info from mii-tool:
```
ross104@ubuntu:~$ sudo mii-tool
eth1: negotiated 1000baseT-[COLOR="Red"]HD[/COLOR] flow-control, link ok

```

Seems mii-tool shows half-duplex link, and ethtool shows full duplex mode...

---

### Post by psusi on 2011-07-19
So both machines are plugged into a gigabit switch, and the switch is plugged into a router?  What is the IP address of the other machine?

---

### Post by ross104 on 2011-07-19
> So both machines are plugged into a gigabit switch, and the switch is plugged into a router? 
Yep! Router, server and other PC are plugged into switch.
> What is the IP address of the other machine?
Router - 10.0.0.1
Server - 10.0.0.200
PC - 10.0.0.2

---

### Post by Entilza on 2011-07-19
Try downloading a large single file from the server through internet and then ping the server from the PC and see if response is slow.

Let's see if we can get torrent out of the picture for reproducing the problem.

---

### Post by ross104 on 2011-07-19
Hmmmm :) That would be tricky but Ill try it tomorrow from work :)
Stay alive for updates :)

---

### Post by ross104 on 2011-07-20
Ok! Tried to transfer file from server over internet and got same lags...

---

### Post by Entilza on 2011-07-20
Now try downloading a large file from the PC through internet then ping the PC from the ubuntu server.

---

### Post by psusi on 2011-07-20
Instead of ping, use traceroute.

---

