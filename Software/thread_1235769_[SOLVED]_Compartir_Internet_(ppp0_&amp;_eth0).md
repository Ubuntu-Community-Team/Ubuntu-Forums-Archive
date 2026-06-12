---
title: "[SOLVED] Compartir Internet (ppp0 &amp; eth0)"
date: 2009-08-09
forum: Software
---

### Post by Leosev on 2009-08-09
Hola que tal, soy nuevo acá. Resulta que instalé ubuntu y no puedo compartir internet. Datos:

PC1: Ubuntu
IP: 192.168.0.1
NetMask: 255.255.255.0
 
PC2: XP
IP: 192.168.0.2
NetMask: 255.255.255.0
GateWay: 192.168.0.1
 
Probé de todo, Firestarter, IPTables, Route (No sé si este último sirve para compartir internet)
 
Dejo Log de ifconfig:.

```
eth0      Link encap:Ethernet  HWaddr 00:e0:7d:b4:df:2c  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe100 

eth1      Link encap:Ethernet  HWaddr 00:13:d3:ba:4d:05  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:feba:4d05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10325 (10.0 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34168 (33.3 KB)  TX bytes:34168 (33.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:201.255.96.85  P-t-P:200.63.148.121  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:9178  Metric:1
          RX packets:780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:687143 (671.0 KB)  TX bytes:209332 (204.4 KB)
```

Log de ROUTE:

```
Destination Gateway Genmask Flags Metric Ref Use Iface
ERRCH01-Lb1.mrs * 255.255.255.255 UH 0 0 0 ppp0
192.168.1.0 * 255.255.255.0 U 0 0 0 eth1
192.168.0.0 * 255.255.255.0 U 0 0 0 eth0
default * 0.0.0.0 U 0 0 0 ppp0
```

Otra cosa más, cuando hago un ping de la PC1 a PC2 no me tira nada( Es como que no tienen conectividad) y viceversa (Ping de PC2 a PC1)

Como verán el problema esta en el modem(ppp0), es un modem USB que estoy manejando con el USB ADSL Modem Manager. (La placa eth1 no le den bola que es otra que tengo ahi para la PS2)

Qué me recomiendan hacer?
Saludos

---

### Post by staar on 2009-08-09
primero que nada, la eth0 no está funcionando, no tenés conectividad, qué estás usando para conectarlas? un switch? un cable cruzado? es lo primero que tenés que solucionar...

segundo, compartir la conexión a internet es fácil, solo tenés que modificar el archivo /etc/sysctl.conf ```
sudo nano /etc/sysctl.conf
``` y poner el valor de esta opción ```
net.ipv4.ip_forward=1
``` en 1

después agregás una regla a iptables así ```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
``` sustiyuendo eth0 por la interface conectada a internet, ppp0 en tu caso, y listo, el único problema es que la regla de iptables se borra al reiniciar, y hay que volver a ponerla, podés usar un script para eso, buscá por el foro que una vez habían descrito una bastante elegante...

saludos

---

### Post by Leosev on 2009-08-09
Listo, tenía las placas de Red al reves que Windows, jaja que ********.

Muchas gracias a los que se tomaron el tiempo de leer xD

Saludos 

(Pueden cerrar el tema)

---

