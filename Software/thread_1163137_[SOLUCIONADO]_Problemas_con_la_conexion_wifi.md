---
title: "[SOLUCIONADO] Problemas con la conexion wifi"
date: 2009-05-18
forum: Software
---

### Post by dnovai on 2009-05-18
Hola amigos! hasta hace un tiempo me he visto en la obligacion de utilizar windows para conectarme a internet (lo cual odio). Resulta que no tener acceso a internet desde Ubuntu OS, logro detectar y conectar el portatil a las redes inlambricas disponibles, pero el problema esta que no tengo acceso a internet (por ejemplo, al intentar conectarme a mi pagina de inicio google.cl me aparece el tipico mensaje de error que el sitio no pudo ser encontrado).
Si sirve de dato tengo lo siguiente en el archivo [COLOR=green]/etc/network/interfaces[/COLOR]:

auto lo 
iface lo inet loopback 

Otro detalle que he intentado utilizando el networkmanger que trae por defecto Ubuntu y con Widc, pero persiste el problema. Ademas el dispositivo inalambrico que me aparece es wlan1 (no debiese ser wlan0?).

Bueno, espero su ayuda.

Saludos!

---

### Post by radixs on 2009-05-18
Si tu proveedor de internet fuera vtr prueba con lo siguiente link
[URL="http://www.ubuntu.cl/e107_plugins/forum/forum_viewtopic.php?457"]
VER[/URL]

---

### Post by Carlos C on 2009-05-18
dnovai: necesitamos más datos para ayudarte. Primero, ¿qué versión de Ubuntu estás usando?, ¿Que proveedor de internet tienes?, ¿Qué modelo de router tienes?, ¿tienes instalado algún tipo de firewall?, ¿Cuál es el modelo de tu tarjeta wifi?

Para ver cómo reconoce el sistema tu tarjeta por favor escribe en el terminal:
```

lspci|grep Ethernet && lspci |grep Wireless && lspci |grep Network
```

También dinos qué obtienes si escribes:
```
iwconfig
```

Es posible que, como sugiere radixs, tengas problemas con tus DNS. Yo siempre recomiendo usar los DNS de opendns:
[http://www.opendns.com/](http://www.opendns.com/)

Saludos.

Pd: Movido a software. Te sugiero mires [acá]("http://ubuntuforums.org/showthread.php?t=1162750").

---

### Post by dnovai on 2009-05-20
Hola amigos!, yo nuevamente. Bueno, les cuento algunos detalles extras. He intentado y probado cosas, pero aun no logro solucionar el problema. Me he dado cuenta de los siguiente:

- Logro ver la página y hacer busquedas en google (eso si que demora bastante), pero al intentar entrar a los links que me arroja la busqueda de google me indica el error de servidor no encontrado.
- Ahora este mensaje lo estoy enviando desde ubuntu, pero desde la universidad, no se cual sera la diferencia, pero aqui no tengo ningun problema.

aqui van los detalles que me pidieron:

root@david-laptop:~# lspci |grep Ethernet
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

root@david-laptop:~# lspci |grep Wireless
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

root@david-laptop:~# lspci |grep Network
(no retorno nada)

root@david-laptop:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty


root@david-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Gloria"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:A3:EF:32   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:6606-B1ED-25C9-E78F-C745-5BBF-BA32-3104-417B-C701-2C1B-7FB1-DDCD-9C81-8B23-602D [2]   Security mode:open
          Power Management:off
          Link Quality=45/100  Signal level:-74 dBm  Noise level=-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



root@david-laptop:~# iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


wlan1     Scan completed :
          Cell 01 - Address: 00:1B:11:A3:EF:32
                    ESSID:"Gloria"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/100  Signal level:-74 dBm  Noise level=-102 dBm
                    Encryption key:on
                    IE: Unknown: 0006476C6F726961
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001e1b8f5dfa
                    Extra: Last beacon: 1360ms ago


root@david-laptop:~# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:3c:2e:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.199 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f8:da:ea
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:e5:fd:07:8a:f2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Bueno, espero su ayuda.

Saludos!

---

### Post by dnovai on 2009-05-20
ah y con respecto al link que me enviaste :

nano /etc/resolv.conf

nameserver 172.17.100.3
nameserver 200.89.70.3
nameserver 200.9.97.3
search uchile.cl cec.uchile.cl


Supongo que son los servidores de la universidad de chile y que por eso puedo conectarme en la universidad.

Ahora si los dejo, saludos!

=)

---

### Post by Carlos C on 2009-05-20
Lo más seguro es que para solucionar tu problema baste con cambiar los DNS por los de opendns.

Saludos.

---

### Post by dnovai on 2009-05-20
disculpa mi ignorancia, como hago eso que me recomiendas?



Saludos!

---

### Post by Carlos C on 2009-05-20
Justamente acabo de responder cómo hacerlo en otro hilo:

[http://ubuntuforums.org/showpost.php?p=7316309&postcount=3](http://ubuntuforums.org/showpost.php?p=7316309&postcount=3)

Saludos!

---

### Post by dnovai on 2009-05-22
Hola!, ahora estoy en la casa de mis padres.
Aquí si pude conectarme a la red wifi sin problemas en mi navegador (Firefox), puedo ver todas las páginas. El proveedor es VTR.

Cuando llegue a Stgo nuevamente e intente conectarme les cuento como me fue.

Saludos y muchas gracias!!

---

### Post by jorval on 2009-05-22
Dnovai. Tengo la misma tarjeta y tuve el mismo problema de no poder conectarme a Internet, pero hace tiempo que lo solucioné con la ayuda de varios ubunteros. Iba a trasladar el tema del Foro a este Sub-foro, pero es muy largo y tedioso, mejor te indico la dirección de la página, léela con atención y verás que después no tendrás más problemas. Saludos.

[http://foros.ubuntu-cl.org/viewtopic.php?t=5864&highlight=]("http://foros.ubuntu-cl.org/viewtopic.php?t=5864&highlight=")

---

### Post by Carlos C on 2009-05-22
> **jorval said:**
> Dnovai. Tengo la misma tarjeta y tuve el mismo problema de no poder conectarme a Internet, pero hace tiempo que lo solucioné con la ayuda de varios ubunteros. Iba a trasladar el tema del Foro a este Sub-foro, pero es muy largo y tedioso, mejor te indico la dirección de la página, léela con atención y verás que después no tendrás más problemas. Saludos.

[http://foros.ubuntu-cl.org/viewtopic.php?t=5864&highlight=](http://foros.ubuntu-cl.org/viewtopic.php?t=5864&highlight=)

jorval, no estoy tan seguro que sea el mismo problema, ya que dnovai dice que puede conectarse a las redes wifi. De ser así es un tema distinto, ya que tiene su tarjeta de red inalámbrica funcionando, pero tiene problemas con el dns. Eso en caso de que un ping al ip de google obtenga respuesta, ahora que lo pienso olvidé preguntar ese detalle.

---

### Post by dnovai on 2009-05-26
Hola amigos! el problema esta resuelto.
Efectivamente el problema era con las DNS  de mi proveedor, en mi caso es telefónica. Solo bastó agregarla (la obtuve desde las propiedades de mi conexión en Windows) al archivo que se explico anteriormente en este hilo.

Gracias a todos por su ayuda.

Adiós!


Seguiré Ubunteando :D

---

