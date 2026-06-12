---
title: "Problemas con Wi-fi en Ubuntu 9.04"
date: 2009-11-29
forum: Software
---

### Post by mujica on 2009-11-29
Hola, ojalá alguien pueda ayudarme a resolver este problema, les cuento...

Actualizé a Ubuntu 9.04 y al principio no tenía los drivers para la tarjeta Broadcom, descargué el paquete *bcm43xx*-*fwcutter* y la tarjeta de red inalámbrica está funcionando. Pero al intentar conectarme a una red inalámbrica el NetworkManager me dice que no puede obtener la IP. Traté de conectarme instalando Wicd pero arrojaba el mismo error. 

He buscado soluciones por todas partes, y lo que a otros les ha funcionado es lo siguiente:

sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid ***EscribeLaESSID***

sudo iwconfig wlan0 key s:***EscribeLaclave_wireless***

sudo dhclient wlan0


Pero a mí me tira el siguiente error: 

[I]Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.[/I]

Así que supongo que tengo un error con la encriptación ¿o no?

Leí que el administrador estándar no acepta el uso de encriptación WAP, sin embargo, en la versión anterior que tenía instalada (8.04) no tuve problemas para conectarme a la red inalámbrica. Además, *wpasupplicant* está instalado.
[COLOR=Navy]
Dejo algunos datos que podrían ayudar:[/COLOR]
[B]
sudo lspci[/B]

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
[B]
sudo ifconfig[/B]

eth0      Link encap:Ethernet  direcciónHW 00:16:36:8b:0e:df  
          Dirección inet6: fe80::216:36ff:fe8b:edf/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:22311 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:22221 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:20925399 (20.9 MB)  TX bytes:4215217 (4.2 MB)
          Interrupción:18 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:20 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:201.222.139.129  P-t-P:10.52.94.3  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:9748 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9313 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:9155158 (9.1 MB)  TX bytes:1603461 (1.6 MB)

wlan0     Link encap:Ethernet  direcciónHW 00:14:a5:f0:03:6a  
          Dirección inet6: fe80::214:a5ff:fef0:36a/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:298 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:310 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:33674 (33.6 KB)  TX bytes:47149 (47.1 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-14-A5-F0-03-6A-33-36-00-00-00-00-00-00-00-00  
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
[B]
sudo iwconfig[/B]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"23defebrero"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
[B]
Y de las redes disponibles, la que me intersa es:
[/B]
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:2B:44:0D
                    ESSID:"23 de febrero"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=76/100  Signal level:-44 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: Unknown: 000D3233206465206665627265726F
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A000110103B00010310470010EA64377B1915608D677F0021912B440D104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000315ede181
                    Extra: Last beacon: 32ms ago


Por últim, si ejecuto *sudo gedit /etc/network/interfaces* aparece lo siguiente en la pestaña "interfaces":

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

Y entiendo que debería haber también una pestaña "wireless", pero no está. Y si trato de abrir /etc/network.d/wireless me dice que no existe el fichero, obviamente... ¿necesito crearlo, cierto? ¿cómo lo hago?

Sorry por un post tan largo, pero ya he buscado por todas partes y no entiendo cómo solucionar mi problema. 

Ojalá alguien sepa cómo ayudarme. Gracias!

---

### Post by mujica on 2009-11-29
Hola, yo de nuevo... 


Bueno, por si todavía alguien puede ayudarme, mi problema es otro ahora :) 

Actualicé al 9.10 para ver si se solucionaba el problema, al principio no, y tuve que instalar un paquete de Broadcom por Synaptic. Después de eso, tengo conexión inalámbrica pero el ícono de la conexión inalámbrica me dice que no estoy conectada.

¿Alguna idea sobre qué puede estar pasando?

---

### Post by Carlos C on 2009-12-01
Qué te aparece si escribes en el terminal:

```
lspci -vnn | grep 14e4
```

Saludos.

---

### Post by moreback on 2009-12-02
> **mujica said:**
> (...) Después de eso, tengo conexión inalámbrica pero el ícono de la conexión inalámbrica me dice que no estoy conectada.

¿Alguna idea sobre qué puede estar pasando?

La configuración de la conexión no la hiciste mediante el Network-Manager, por lo cual éste no puede manejarla y por eso te indica como si estuvieras desconectada.

---

