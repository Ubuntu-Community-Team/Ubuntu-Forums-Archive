---
title: "Virtualbox Guest gateway issue after change to bridged networking"
date: 2009-12-21
forum: Virtualisation
---

### Post by dennisbinkhorst on 2009-12-21
Hi all,

I needed SSH access from my host machine to a guest machine in Ubuntu 9.10. I changed the network settings for the guest machine from NAT to BRIDGED. To accomplish this I followed instructions as given on the link below:

[http://muffinresearch.co.uk/archives/2009/04/08/virtualbox-access-guests-via-a-virtual-interface/](http://muffinresearch.co.uk/archives/2009/04/08/virtualbox-access-guests-via-a-virtual-interface/)

So far, so good: I am now able to connect to the Virtualbox guest machine from the host.

However, I am now facing the next problem: I cannot connect to the internet anymore from the guest machine. I am able to connect to the host IP, and the host itself has a working internet connection as well.

I feel I need to edit something in  /etc/network/interfaces, however I'm not sure what to edit there In order to get my internet connection back, nor am I sure if I'm heading in the right direction at all.

Any help would be greatly appreciated!

Thanks.

---

### Post by lmarmisa on 2009-12-21
Have you any type of limitation in your LAN for the connection to Internet?. 

Before the change, your guest computer accessed to Internet using the private IP address of the host computer (double NAT). Now the guest computer has a different private IP address in your LAN (probably negotiated with DHCP):

```

ifconfig

```Is this other local  IP address allowed to connect to Internet?.

Best regards,

Luis

---

### Post by muffinresearch on 2009-12-22
You need two interfaces one is NAT for outbound internet access and the other is the host-only (referred to as bridged in more recent VirtualBox version) connection for internal communication e.g. via SSH.

Sounds like you changed your NAT interface to bridged so what you need to do is create a second interface which is NAT - that should then mean you'll be able to access the internet again.

---

### Post by dennisbinkhorst on 2009-12-22
Hi Luis and Muffinresearch, thanks for your quick replies.

In order to make it a bit clearer on how my current configuration is set up, you find the code and network settings below.

**HOST machine [nx001], Ubuntu 9.10. Karmic 64-bit:**

- Internet connection is up and running (I'm replying from this machine right now)
- Connected to gateway 192.168.20.254

*# /etc/network/interfaces*
```

auto lo wlan0
iface lo inet loopback

auto tap0
iface tap0 inet manual
        up ifconfig $IFACE 10.0.2.1 netmask 255.255.255.0 up
        down ifconfig $IFACE down
        tunctl_user dennis


```*# ifconfig* (eth0 IP-address from DHCP)
```

eth0      Link encap:Ethernet  HWaddr 00:26:22:4a:04:e8  
          inet addr:192.168.20.148  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe4a:4e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848592 (848.5 KB)  TX bytes:197077 (197.0 KB)
          Interrupt:30 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

tap0      Link encap:Ethernet  HWaddr ae:d7:54:9a:d4:a9  
          inet addr:10.0.2.1  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::acd7:54ff:fe9a:d4a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:62 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```*# VirtualBox setup for VM [vsx001]:*
- PCnet-FAST III (Bridged adapter, tap0)

**GUEST machine [vsx001], Fedora 12 32-bit:**

*# ifconfig* (eth0 static IP-address)
```

eth0      Link encap:Ethernet  HWaddr 08:00:27:67:DC:8F  
          inet addr:10.0.2.100  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe67:dc8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5051 (4.9 KiB)  TX bytes:8872 (8.6 KiB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190 (190.0 b)  TX bytes:190 (190.0 b)

```Muffinresearch, the part where you recommend to create a second interface setup for NAT next to the BRIDGED interface. I really don't understand where I should create this. On the HOST or the GUEST machine?

Ik hope the network settings I wrote down above make things clearer.

Hope to hear from you soon.

Thanks!

---

### Post by dennisbinkhorst on 2009-12-22
Hi, I just found the article below on Virtualbox.org. 
This seems to cover my preferred setup. Will give it a try and report back.

[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

---

### Post by lmarmisa on 2009-12-23
I do not need to create any **tap** interface. Simply I define the Bridge mode in The Adapter 1 of the network interface menu (Enable Network Adapter; PCnet-Fast III (Am79C973); Bridged Adapter; etho). No other adapter is used in my case.

My Ubuntu guest system negotiates an IP addess of my LAN using DHCP. There are two independent LAN IP addresses: one for the host computer; a second IP address for the guest system.

VM has no problem of communication both with Internet and with other PCs in my LAN, including the host computer.

This simple solution works fine in my computer.

*# /etc/network/interfaces (both systems)*
```

auto lo
iface lo inet loopback

```*ifconfig (guest system)*
```

eth0      Link encap:Ethernet  direccionHW 08:00:27:6d:19:dc  
          Direc. inet:**192.168.1.143**  Difus.:192.168.1.255  Masc:255.255.255.0
          Direccion inet6: fe80::a00:27ff:fe6d:19dc/64 Alcance:Enlace
          ACTIVO DIFUSION FUNCIONANDO MULTICAST  MTU:1500  Metrica:1
          Paquetes RX:588 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:242 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:72132 (72.1 KB)  TX bytes:31844 (31.8 KB)
          Interrupcion:11 Direccion base: 0xd020 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Masc:255.0.0.0
          Direccion inet6: ::1/128 Alcance:Anfitrion
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Metrica:1
          Paquetes RX:8 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:440 (440.0 B)  TX bytes:440 (440.0 B)



```*ifconfig (host system)*
```

eth0      Link encap:Ethernet  direccionHW 00:50:fc:a2:d2:46  
          Direc. inet:**192.168.1.132**  Difus.:192.168.1.255  Masc:255.255.255.0
          Direccion inet6: fe80::250:fcff:fea2:d246/64 Alcance:Enlace
          ACTIVO DIFUSION FUNCIONANDO MULTICAST  MTU:1500  Metrica:1
          Paquetes RX:1362 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:394 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:274253 (274.2 KB)  TX bytes:51375 (51.3 KB)
          Interrupcion:3 Direccion base: 0xd400 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Masc:255.0.0.0
          Direccion inet6: ::1/128 Alcance:Anfitrion
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Metrica:1
          Paquetes RX:8 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:480 (480.0 B)  TX bytes:480 (480.0 B)


```The version of my VirtualBox is 3.0.12.

Best regards,

Luis

---

### Post by dennisbinkhorst on 2009-12-23
Hi Luis,

Thanks again for your efforts to get this thing working for me. 
First of all: Your method works just fine: the VM as well as the host system can connect to each other and the internet. 
This is definitely the most straight forward approach, and quite usable.

Thanks again,

Dennis

---

### Post by SecretCode on 2009-12-23
> **muffinresearch said:**
> You need two interfaces one is NAT for outbound internet access and the other is the host-only (referred to as bridged in more recent VirtualBox version) connection for internal communication e.g. via SSH.

Sounds like you changed your NAT interface to bridged so what you need to do is create a second interface which is NAT - that should then mean you'll be able to access the internet again.

For the record this isn't correct - host-only and bridged interfaces are different things. A guest with a host-only interface won't be able to access the outside world, but both NAT and bridged interfaces should allow it. I don't understand the role of the tap0 interface on the host, but I expect that's related to why the guest couldn't connect with a bridged interface. (With NAT it can use any tunnelled connection the host has set up, but with a bridged connection it would have to do all that itself.)

Dennis, what are the ifconfig outputs on your host and guest now that you have it working?

---

### Post by muffinresearch on 2010-01-06
> **SecretCode said:**
> For the record this isn't correct - host-only and bridged interfaces are different things.

Strictly speaking you are right. However, back in version 2.x of VirtualBox when I wrote my article, if memory serves bridged and host-only interfaces didn't exist there was just 'Host interface' networking. Using that with a TAP interface ([http://en.wikipedia.org/wiki/TUN/TAP](http://en.wikipedia.org/wiki/TUN/TAP)) is essentially the same as Using bridging in 3.x with a TAP interface.

The added benefit that springs to mind is that using a TAP interface with an additional NAT interface on the Guest is that it will still be working when you move from Wireless to wired network whereas bridging to physical interfaces may cause you problems. But if you're using this on a desktop this may not be an issue for you.

---

