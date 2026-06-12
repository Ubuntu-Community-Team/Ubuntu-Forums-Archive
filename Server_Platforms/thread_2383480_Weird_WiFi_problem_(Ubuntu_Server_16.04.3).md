---
title: "Weird WiFi problem (Ubuntu Server 16.04.3)"
date: 2018-01-25
forum: Server Platforms
---

### Post by renaud11232 on 2018-01-25
Hello,

I recently bought a OrangePi Lite and put Armbian 5.35 Ubuntu Server on it.
I tried to connect to a wifi which looked like it worked.
But I then have weird network problems.

The device is unreachable (no ping, "no route to host" when i try to ssh onto it) until I ping another device with it.
If I do that the first few packets are lost, then once the device answers, they can both communicate.
Same problem happens with USB Wireless Adapter.

I have no idea where that comes from.

I opened a thread on the armbian forums, but in case it is independent from the board I also ask it here.
The thread : [https://forum.armbian.com/topic/6257-orange-pi-lite-weird-wifi-problem/](https://forum.armbian.com/topic/6257-orange-pi-lite-weird-wifi-problem/)

Thanks for any upcomming help.


Output of the ifconfig -a command : 
```

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.93  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::1028:a2c1:f12:85f9  prefixlen 64  scopeid 0x20<link>
        ether 02:81:62:bd:97:0e  txqueuelen 1000  (Ethernet)
        RX packets 512  bytes 64192 (62.6 KiB)
        RX errors 0  dropped 1291  overruns 0  frame 0
        TX packets 513  bytes 59689 (58.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

---

