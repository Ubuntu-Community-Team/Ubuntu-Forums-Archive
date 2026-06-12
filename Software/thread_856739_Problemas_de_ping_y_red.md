---
title: "Problemas de ping y red"
date: 2008-07-11
forum: Software
---

### Post by el.demiurgo on 2008-07-11
Hola a todos,
Instalé Ubuntu por primera vez (H. Heron) hace unos meses. Anda todo bien pero tengo problemas para hacer algunas cosas de red.
Mi máquina tiene una placa inalámbrica y otra común. EN mi red (usando un router d-link) tengo además una notebook con XP, una XBOX y una XBOX360. 
Cuando conecto todo por medio de cable, no tengo problema ninguno. Ahora, cuando uso wireless no puedo hacer lo siguiente:
-hacer ping al router o a las consolas (de la notebook con XP no hay problema)
-ver la página de configuración del router
-compartir archivos

Lo gracioso es que cuando uso la placa común puedo hacer todo.

Alguien sabe qué puede ser esto?

Por lo que veo, tampoco tengo el firewall prendido pero no me doy cuenta bien cómo chequearlo.... (iptables?)

Usando ifconfig me da esto:
eth0 Link encap:Ethernet HWaddr 00:0e:a6:bc:dc:59
inet addr:192.168.0.201 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2128 errors:0 dropped:0 overruns:0 frame:0
TX packets:2128 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:133171 (130.0 KB) TX bytes:133171 (130.0 KB)

wlan0 Link encap:Ethernet HWaddr 00:19:5b:80:03:19
inet addr:192.168.0.109 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::219:5bff:fe80:319/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4859 errors:0 dropped:0 overruns:0 frame:0
TX packets:4897 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2175495 (2.0 MB) TX bytes:810932 (791.9 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-19-5B-80-03-19-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


Gracias!

---

### Post by VitaLiNux on 2008-07-11
Hola,

Puedes revisar si tu firewall está activado con el siguiente comando:

sudo /etc/init.d/firestarter status

En cuanto a lo de tu tarjeta inalámbrica, sería bueno que dijeras la marca y el modelo que usas.

---

### Post by el.demiurgo on 2008-07-11
Hola VitaLiNux,
No tengo el firestarter instalado. Nunca lo puse..

La placa es una d-link, al igual que el router (estando en XP andaba perfecto). Es DWL 510.

Ahora no me acuerdo el modelo. Me llama la atención que pueda ver internet y no pueda ver otras cosas, por eso creo que es alguna especie de Firewall o algo así.

---

### Post by el.demiurgo on 2008-07-11
Como te decía, la placa es una d-link GWL 510

Cuando haces lshw te tira:
description: Wireless interface
product: RT2561/RT61 rev B 802.11g
vendor: RaLink

Sirve esto?

---

### Post by faktorqm on 2008-07-12
Hola, si tenes internet en todos lados, cual es el problema? no tener ping significa tener el trafico ICMP deshabilitado en algun punto de paso de la red, ahora, vos lo necesitas eso?

Para compartir archivos, te anda todo ok? acá explico yo mismo como se hace para compartir archivos.
[http://ubuntuforums.org/showthread.php?t=697717&highlight=compartir+archivos](http://ubuntuforums.org/showthread.php?t=697717&highlight=compartir+archivos) los puertos miralo en la sección faq de ese mismo tutorial.

Para ver el estado de iptables encontre esto: [http://www.forosdelweb.com/f41/conocer-estado-iptables-294390/](http://www.forosdelweb.com/f41/conocer-estado-iptables-294390/) no se si te sirve. Salu2!!

---

### Post by el.demiurgo on 2008-07-12
Hola faktorqm,
Gracias por tu ayuda.

El problema es que tengo todo compartido y funciona cuando uso la placa con cable pero yo quiero usar la wireless.

El ping en sí mismo no me importa nada pero el hecho de no poder ver la máquina desde los otros elementos por wireless le quita la funcionalidad que tenía en XP.

Yo uso la XBOX como media center y quiero mirar toda la música/videos que tengo en la PC con ubuntu pero ahora no puedo porque ni siquiera veo la máquina.

En resumen, no me doy cuenta cómo hacer para que el resto de la red vea la máquina en desde la placa wireless.
Gracias.

---

### Post by eldragon on 2008-07-12
cuando estes con wireless hace 
```

sudo ifdown eth0

```

y fijate si anda todo bien...

cuando estes con cable, hace
```

sudo ifup eth0

```


me parece que esta routeando la lan por eth0 siempre, no se da cuenta que el cable esta desconectado.

---

### Post by el.demiurgo on 2008-07-12
Hola,
Finalmente lo resolví (de casualidad).

Estaba jugando con las configuraciones de red y desmarqué la opción Roaming en el adaptador de red normal y se arregló todo. No tengo idea porqué pero bueno....

Gracias a todos por su ayuda y su tiempo!

---

