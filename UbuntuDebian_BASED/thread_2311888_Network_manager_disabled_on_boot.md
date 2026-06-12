---
title: "Network manager disabled on boot"
date: 2016-01-30
forum: Ubuntu/Debian BASED
---

### Post by adonai2 on 2016-01-30
Im running LXLE (lubuntu based) dual boot with Windows 8.1
Recently I installed 3.13.0-77-generic headers and everything was fine until I did a reboot and chose 3.13.0-65-generic. My network was disabled as [this image]("http://i.stack.imgur.com/HGAIS.jpg") indicates and everytime I do

```
$ sudo service network-manager status
```
I get:
```
network-status stop/waiting
```

I tried several solutions
In /etc/network/interfaces I did:
```
 # interfaces(5) file used by ifup(8) and ifdown(8)
 auto lo
 iface lo inet loopback

 auto eth0
 iface eth0 inet dhcp

 auto wlan0  iface wlan0 inet dhcp
```


Also I deleted /var/lib/NetworkManager/NetworkManager.state and restarted but always get:
```
 [main]
 NetworkingEnabled=true
 WirelessEnabled=true
 WWANEnabled=true  WimaxEnabled=true
```


This is the output of ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr a0:48:1c:e9:bd:23             UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:1175 errors:0 dropped:0 overruns:0 frame:0
           TX packets:1175 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:106331 (106.3 KB)  TX bytes:106331 (106.3 KB)

 virbr0    Link encap:Ethernet  HWaddr ee:81:01:14:b8:75  
           inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 wlan0     Link encap:Ethernet  HWaddr 48:d2:24:ae:88:a5  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


By the way the network is working fine on Windows.

UPDATE
I removed the 3.13.0-77 headers and nothing changed

---

### Post by howefield on 2016-01-30
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by matt_symes on 2016-01-30
Hi

You don't want both your interfaces file and network manager trying to manage the same interfaces, so those changes to your interfaces file need to be removed.

Open a terminal and copy and paste this into it. It'll remove those entries.

```
sudo sed -i '/eth0/d;/wlan0/d' /etc/network/interfaces
```

As for the file

```
/var/lib/NetworkManager/NetworkManager.state
```

you want network-manager to create that each time.

So, i suspect the problem lies elsewhere.

To help, can you post the the output of (capital A below)

```
lspci -nnk | grep -iA2 wireless
```

Next, open a terminal and type

```
tail -n0 -f /var/log/syslog
```

Open up a second terminal and type

```
sudo service network-manager start
```

Post the output that appears in the first terminal window into your next post.

Hopefully that'll give people something to start with.

Kind regards

---

### Post by matt_symes on 2016-01-30
Hi

Take a look at this thread and the link posted in it.

[http://ubuntuforums.org/showthread.php?t=2311891&p=13431787#post13431787](http://ubuntuforums.org/showthread.php?t=2311891&p=13431787#post13431787)

Kind regards

---

### Post by adonai2 on 2016-01-31
Great that solved it!
Thank you so much

---

