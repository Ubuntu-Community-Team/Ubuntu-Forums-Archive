---
title: "Ubunt server network card not working :("
date: 2010-05-10
forum: Server Platforms
---

### Post by konnorrigby on 2010-05-10
Ok so i just downloaded Ubuntu Server 10.04 and i'm very happy with it on my virtual machine... but when i try to install it on my actual server it fails.

   When i went to install it, it told me that there was no network hardware detected or something like that. So i just thought i could install a driver for it later. 
   
   So other than that all went well. and im very happy but now i dont know how to install my network driver. The card is a LYNKSYS LNE100TX. i downloaded the driver software and burnt it to disk because i was out of floppys. (I like floppys better:)) and when i went to install the software it allmost worked but it said:

```

make: gcc command not found

```
 I'm assuming that means i need to install gcc but didn't really know how to go about it having no internet. So if someone could help me out here it would be much appreciated. Thanks in advance.

--Konnor

---

### Post by windependence on 2010-05-10
What is the output of:

```
sudo ifconfig -a
```

-Tim

---

### Post by konnorrigby on 2010-05-10
```


root@home-server:~# ifconfig -a
eth0         Link encap:Ethernet  HWaddr 00:0c:41:1e:a2:63
               BROADCAST MULTICAST  MTU:1500  Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
               callisions:0 txqueuelen:1000
               RX bytes:0 (0,0 B)  TX bytes:0 (0,0 B)
               Interupt:11 Base address:0xe800

lo            Link encap:Local:Loopback
               inett addr:127.0.0.1  Mask:255.0.0.0
               inet6 addr:  ::1/208 Scope:Host               
               UP LOOPBACK RUNNING  MTU:16436  Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
               callisions:0 txqueuelen:1000
               RX bytes:0 (0,0 B)  TX bytes:0 (0,0 B)





```

---

### Post by konnorrigby on 2010-05-12
bump

---

### Post by jw12321 on 2010-07-31
bump

---

### Post by jw12321 on 2010-07-31
Does this help you?

```
sudo rmmod tulip
sudo modprobe tulip options=5
```

This worked for me.

---

### Post by spynappels on 2010-07-31
Can you post the output of /etc/network/interfaces please? The fact that you have an eth0 entry at all when you run ifconfig means a network card is detected, so we maybe only have to edit the interfaces file.

---

