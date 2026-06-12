---
title: "Gibabyte network interface connects at 100Mb/s to gigabyte switch"
date: 2008-10-01
forum: Server Platforms
---

### Post by ezacon on 2008-10-01
I have replaced the switch with a gigabyte one.
The switch port is correctly configured and works at gigabyte with other devices.
The ubuntu 8.04 server connects at 100, according to switch indicators. The nic interface of the server is gigabyte.

here is some aditional info:

lspci: 
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

lsmod:
e1000                 144704  0

ifconfig:
eth0      Link encap:Ethernet  direcciónHW 00:19:d1:99:f8:c2
          inet dirección:192.168.1.1  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::219:d1ff:fe99:f8c2/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:2021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2879 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:100
          RX bytes:146215 (142.7 KB)  TX bytes:3518269 (3.3 MB)
          Dirección base: 0x30e0 Memoria:e0300000-e0320000


How can i know in console the speed of the nic?
how can i control the speed link?
thanks

---

### Post by dannyboy79 on 2008-10-01
this be of asssistance to you:
[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by ezacon on 2008-10-01
exactely what im looking for.
ethtool and net-tools are even installed by default in my server.
ethtool worked for me.

Thanks Dannyboy79

---

