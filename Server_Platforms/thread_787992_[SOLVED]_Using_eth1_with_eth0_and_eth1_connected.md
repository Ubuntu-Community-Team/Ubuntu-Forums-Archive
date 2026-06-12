---
title: "[SOLVED] Using eth1 with eth0 and eth1 connected"
date: 2008-05-09
forum: Server Platforms
---

### Post by altonbr on 2008-05-09
I usually have one network connections from one LAN but I need to backup my server on my other LAN so now I have my server plugged in to both.

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:D0:48:14  
          inet addr:192.168.1.170  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fed0:4814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:641393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:892055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83927809 (80.0 MiB)  TX bytes:1084548573 (1.0 GiB)
          Interrupt:16 Memory:f8000000-f8012100 

eth1      Link encap:Ethernet  HWaddr 00:19:B9:D0:48:16  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fed0:4816/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2451 (2.3 KiB)  TX bytes:5803 (5.6 KiB)
          Interrupt:16 Memory:f4000000-f4012100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71260 (69.5 KiB)  TX bytes:71260 (69.5 KiB)
```

eth0 is what the server normally runs on, but eth1 is the new LAN.

I want to SCP to 192.168.1.2 on eth1 but whenever I run scp or ssh, it seems to run on eth0. How can I get those services to run on eth1?

---

### Post by mrsteveman1 on 2008-05-09
It sounds like you have all this stuff connected to the same switch, and those are definitely the same subnet on eth0 and eth1, so they really aren't separate lans.

Am i correct here?

---

### Post by altonbr on 2008-05-09
> **mrsteveman1 said:**
> It sounds like you have all this stuff connected to the same switch, and those are definitely the same subnet on eth0 and eth1, so they really aren't separate lans.

Am i correct here?

Two routers, two switches, two NIC cards.

They are just both Class-C networks as they're both identical Linksys routers.

One network is my home network and the other is for my servers.

---

### Post by songshu on 2008-05-09
as far as i know it would choose its path by network and not by interface, altough someone might know a way to force it.

changing the network typology to eth0 192.168.1.170 and eth 192.168.2.114 as mrsteveman1 said would solve the problem forever, but it might not be worth the trouble for a one time afair.

you could disable eth0 for the time being, as a temporary fix.

what you also could do is to initiate it from the other machine 192.168.1.2

like so 

scp yourname@192.168.1.114:/file/tobackup /end/locationforbackup

---

### Post by altonbr on 2008-05-09
> **songshu said:**
> as far as i know it would choose its path by network and not by interface, altough someone might know a way to force it.

changing the network typology to eth0 192.168.1.170 and eth 192.168.2.114 as mrsteveman1 said would solve the problem forever, but it might not be worth the trouble for a one time afair.

you could disable eth0 for the time being, as a temporary fix.

what you also could do is to initiate it from the other machine 192.168.1.2

like so 

scp yourname@192.168.1.114:/file/tobackup /end/locationforbackup

I wish I could, but the computers on that network can't talk to it. I'll see if taking down eth0 will help. Thank you.

EDIT::
Yup, running
```
sudo ifdown eth0
```
brought eth1 up. Thank you guys.

---

### Post by ilrudie on 2008-05-09
You could add a static route that would specify when you enter such and such ip address or ip range use this interface and this gateway.  see man route for information on adding routes.  As a side note any routes added with the route add command are temporary and will disappear after a reboot.  To make the route permanent add it to the /etc/network/interfaces file.  More info can be found here: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Debian_.2F_Ubuntu_Network_Configuration](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Debian_.2F_Ubuntu_Network_Configuration)

hope that helps

---

### Post by gtdaqua on 2008-05-10
eth0 and eth1 are both connected to 192.168.1.0 network. There are no two different networks here. Even without default gateway configured you should be able to contact any 192.168.1.x device through L2-broadcasting.

---

### Post by mrsteveman1 on 2008-05-12
If i didn't say this clearly before as others did, a machine with 2 nics, going to 2 switches and 2 different routers, but using the same subnet on both of them, will ALWAYS have a broken routing table.

You will end up with 2 different routes in the table, going to the same subnet on 2 different interfaces which don't ever intersect. It is ok to do this if you have redundant interfaces and a metric on the interface to make one a backup, but otherwise it breaks routing quite a bit and leads to problems.

---

### Post by altonbr on 2008-05-12
> **mrsteveman1 said:**
> If i didn't say this clearly before as others did, a machine with 2 nics, going to 2 switches and 2 different routers, but using the same subnet on both of them, will ALWAYS have a broken routing table.

You will end up with 2 different routes in the table, going to the same subnet on 2 different interfaces which don't ever intersect. It is ok to do this if you have redundant interfaces and a metric on the interface to make one a backup, but otherwise it breaks routing quite a bit and leads to problems.

So is a route such as 'ilrudie' suggested in order? Or how do I change the subnet mask on one router?

---

### Post by mrsteveman1 on 2008-05-12
The mask is fine, you just need to change the third subnet number so they are different.

with a 255.255.255.0 network mask, changing 192.168.1.x to 192.168.2.x is a different network. This will completely separate the 2 networks and should make it very clear which interface specific traffic is supposed to be using.

Do you have 2 separate internet connections? Why are there 2 routers?

---

### Post by altonbr on 2008-05-13
> **mrsteveman1 said:**
> The mask is fine, you just need to change the third subnet number so they are different.

with a 255.255.255.0 network mask, changing 192.168.1.x to 192.168.2.x is a different network. This will completely separate the 2 networks and should make it very clear which interface specific traffic is supposed to be using.

Do you have 2 separate internet connections? Why are there 2 routers?

Okay, I hope my Linksys/Cisco router supports changing 192.168.1.x to 192.168.2.x

I have to ethernet connections/2 routers/2 modems because one is for office use and the other is for personal use. I just wanted to backup my office server on my personal network (or at least try).

---

### Post by mrsteveman1 on 2008-05-13
Yea there's nothing weird there, it should work just fine. All these routers support changing the network of course.

I'm barely awake at the moment so I can't visualize what all this looks like, but if all you want to do is connect the server to your home network to pull data off of it things should work, just make sure whatever services you have running on that server are listening on the NIC for your home network so you can get to them.

---

