---
title: "icmpv6_send: no reply to icmp error"
date: 2012-03-26
forum: Server Platforms
---

### Post by fl5x on 2012-03-26
Hi, I'm getting this error every two minutes in my /var/log/syslog.

kernel: [392954.360034] icmpv6_send: no reply to icmp error
kernel: [393025.890027] icmpv6_send: no reply to icmp error
kernel: [393254.830033] icmpv6_send: no reply to icmp error


I don't know what it means. Is there anything wrong with my Ubuntu 10.04 server ?

Thanks.

---

### Post by sanderj on 2012-03-26
What's the output of "ifconfig"?

And are you running this on real hardware, or in a virtual machine?

---

### Post by fl5x on 2012-03-26
It's real hardware.

eth0      Link encap:Ethernet  direcciónHW 00:1f:d0:bf:8d:ec  
          Direc. inet:150.214.196.123  Difus.:150.214.197.255  Másc:255.255.254.0
          Dirección inet6: fec0::9:21f:d0ff:febf:8dec/64 Alcance:Sitio
          Dirección inet6: 2002:96d6:c55c:9:21f:d0ff:febf:8dec/64 Alcance:Global
          Dirección inet6: fe80::21f:d0ff:febf:8dec/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3165702 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:901161 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1570952863 (1.5 GB)  TX bytes:308178876 (308.1 MB)
          Interrupción:26 Dirección base: 0xc000 

eth1      Link encap:Ethernet  direcciónHW 00:0c:76:00:fd:d2  
          Direc. inet:192.168.0.1  Difus.:192.168.0.255  Másc:255.255.255.224
          Dirección inet6: fe80::20c:76ff:fe00:fdd2/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:593925 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:919668 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:110859505 (110.8 MB)  TX bytes:1046700889 (1.0 GB)
          Interrupción:21 Dirección base: 0x6000

---

### Post by sanderj on 2012-03-26
You have a 2002:96d6:c55c:... address, so you have 6to4 activated, right? Can you "ping6 ipv6.google.com"?

And eth0 has a public IPv4 address, so this system is directly connected to Internet? Is it a kind of gateway, as it has an eth1 (with private IPv4) too?

---

### Post by fl5x on 2012-03-26
Not sure if I have 6to4 activated, at least it was not activated on purpose. Can be that the reason for the error?  

I can't ping "ping6 ipv6.google.com"
connect: Network is unreachable

Eth0 is directly connected to Internet and Eth1 is connected to Intranet as it is explained here: [http://www.somewhereville.com/?p=1196](http://www.somewhereville.com/?p=1196)

Thanks for helping!

---

### Post by sanderj on 2012-03-26
That 6to4 address could be the reason your system thinks there is IPv6, does something, which leads to the error message (because IPv6 is not working).

There are two ways that the 6to4 2002: address can have landed on your Linux system:
1) a router building up the 6to4 tunnel, and distributing 2002: address on your LAN. However: your system has a public IP address, so a router doing NAT is unlikely.
2) your Linux system having a 6to4 tunnel itself (although I don't see a tunnel interface in your ifconfig). See [http://ubuntuforums.org/showthread.php?p=10939087](http://ubuntuforums.org/showthread.php?p=10939087) how to create such a tunnel; hopefully it will give an idea how to remove it

Another possibility is to go *forward* and make the IPv6 working. I would prefer that (see my sig).

---

### Post by sanderj on 2012-03-26
PS:

"rdisc6" is a nice tool to listen for IPv6-address-broadcasts:

rdisc6 -1 -r1 -q wlan0
rdisc6 -1 -r1 -q eth0

If there is a router advertising IPv6, you will get a response ...

---

### Post by fl5x on 2012-03-27
Well, I'm not sure I need IPv6, actually I've disabled it and the error is gone.

$ sudo nano /etc/sysctl.conf

Then these lines were added:

# IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Could this problem has something to do with avahi-daemon? I was getting errors until it was restarted.

$ sudo restart avahi-daemon

PS. I can't ping localhost. Isn't it weird?

---

### Post by fl5x on 2012-03-27
After this:

$ ifconfig | grep lo $ sudo /sbin/ifconfig lo 127.0.0.1 up 
I get this:
$ ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1f:d0:bf:8d:ec  
          Direc. inet:150.214.196.123  Difus.:150.214.197.255  Másc:255.255.254.0
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:4018297 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1174822 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1890428697 (1.8 GB)  TX bytes:416260902 (416.2 MB)
          Interrupción:26 Dirección base: 0xc000 

eth1      Link encap:Ethernet  direcciónHW 00:0c:76:00:fd:d2  
          Direc. inet:192.168.0.1  Difus.:192.168.0.255  Másc:255.255.255.224
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:763562 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1129403 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:156109149 (156.1 MB)  TX bytes:1227315193 (1.2 GB)
          Interrupción:21 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:46 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3385 (3.3 KB)  TX bytes:3385 (3.3 KB)

Now I'm able to ping localhost.

Why didn't "lo" show up first?

---

