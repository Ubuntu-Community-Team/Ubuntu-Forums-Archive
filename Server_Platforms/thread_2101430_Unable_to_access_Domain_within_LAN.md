---
title: "Unable to access Domain within LAN"
date: 2013-01-04
forum: Server Platforms
---

### Post by LinuxEater on 2013-01-04
Alright, so I did a fair bit of searching through the forums before posting this. I'm currently running Ubuntu Server 12.08, and I've got LAMP going and everything is set up nicely. The only problem I'm running into is the fact that I can't access my domain from inside my LAN. A check with a proxy shows that it works, it just won't resolve within. I have my ports forwarded and my ISP does not block port 80. I can access it from the 192.168.1.132 internal on the LAN as well.

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:18:f3:10:70:b3  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe10:70b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3410432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3072634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:434259049 (434.2 MB)  TX bytes:1758980858 (1.7 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19036664 (19.0 MB)  TX bytes:19036664 (19.0 MB)

/etc/hosts
> 127.0.0.1       localhost
127.0.1.1       butlertron
#192.168.1.*            frostglass.zapto.org
#216.xxx.xx.xxx         frostglass.zapto.org

The reason the bottom two are commented out there, I saw some posts saying that putting those addresses in might work, but to no avail. If you need any other information, let me know and I'll happily give it to you!

Generally I'm an Archlinux user, and this is my first time playing with Ubuntu since 7.04 or something, so it's been a long-*** time.

EDIT: It seems external users are being directed to 192.168.1.132, which is the internal IP for the server. D:

---

### Post by volkswagner on 2013-01-04
Change your /etc/hosts to include:

```
192.168.1.132 frostglass.zapto.org
```

This is likely an issue with NAT and your router.

The entry above is for client machines on the LAN, not the server itself.

From a LAN machine run the following command.
```
host frostglass.zapto.org
```

This should return your external ip.  After change /etc/hosts run the command again and it should return your internal ip.

Check your router, possibly security settings for NAT traverse or similar.

---

### Post by LinuxEater on 2013-01-04
> **volkswagner said:**
> Change your /etc/hosts to include:

```
192.168.1.132 frostglass.zapto.org
```

This is likely an issue with NAT and your router.

The entry above is for client machines on the LAN, not the server itself.

From a LAN machine run the following command.
```
host frostglass.zapto.org
```

This should return your external ip.  After change /etc/hosts run the command again and it should return your internal ip.

Check your router, possibly security settings for NAT traverse or similar.

Why do I have to change the hosts files on the client machines? I've never had to do that with any other distro. I really appreciate the help, don't get me wrong, I'm just confused! I've never had to change any NAT settings on my for Archlinux, everything just ran out of the box after I forward the port. Like I said, just really confused.

The host frostglass.zapto.org command returned my external IP after changing the hosts file, but I still can't access the website.

EDIT: I guess after editting my own hosts file, it seems to be working, it's just bizarre as I've *never* had to do that before.

---

