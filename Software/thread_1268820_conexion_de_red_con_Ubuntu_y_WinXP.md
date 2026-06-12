---
title: "conexion de red con Ubuntu y WinXP"
date: 2009-09-17
forum: Software
---

### Post by sebastian kraus on 2009-09-17
hola es mi primera consulta en este foro, me he decidido cambiar a ubuntu y mi duda es como configuro la red para compartir internet desde una maquina con xp a la mia con ubuntu por intuicion llegue a que se conecten en red las maquinas, es decir que aparezca como conectada la red... pero en la pc con linux no tngo internet y ademas tampoco puedo ver el equipo con xp en la red.Si alguien puede darme una ayuda lo agradeceria la verdad q yo de redes 0:lolflag:
 
 
espero su respuesta

---

### Post by staar on 2009-09-17
algunas preguntas, como se conecta a internet la máquina con xp? como están conectadas las máquinas? hay algún switch, router, etc?

saludos

---

### Post by guillermolisi on 2009-09-17
Edite el asunto del thread para que sea mas especifico con su contenido.

Movido a Software.

---

### Post by ALEXEX on 2009-09-17
hola.
 
estan conectadas atraves de un router?
 
ahora, en caso de que sea asi, cuenta con wireless, red inalambrica?

---

### Post by sebastian kraus on 2009-09-17
estan conectadas por un cable cruzado digamos directo entre dos maquinas  la conexion a internet es desde un modem usb

---

### Post by Hei Ku on 2009-09-17
Podes correr ifconfig en el ubuntu y postear aca el resultado?

---

### Post by sebastian kraus on 2009-09-17
eth0      Link encap:Ethernet  direcciónHW 00:11:d8:71:7f:b5  
          inet dirección:127.0.0.1  Difusión:127.0.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:d8ff:fe71:7fb5/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:357 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:13786 (13.7 KB)  TX bytes:98844 (98.8 KB)
          Interrupción:23 Dirección base: 0x4000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:54660 (54.6 KB)  TX bytes:54660 (54.6 KB)

---

### Post by Hei Ku on 2009-09-17
Postea por favor tu archivo /etc/network/interfaces

Imagino que no tenes el XP configurado como DHCP, no? Si no, postea la configuracion de red del XP tambien.

---

### Post by sebastian kraus on 2009-09-17
m pueden decir como configurarla como dchp por q la verdad si no ni idea xd:lolflag:

---

### Post by Hei Ku on 2009-09-17
Esa es una pregunta para el foro de Windows. ;)

No pusiste el archivo que te pedí, ni la configuración de red de windows.

---

### Post by sebastian kraus on 2009-09-17
el problema es q ni idea de redes yo no entienden :P

---

### Post by Hei Ku on 2009-09-17
Podrias por favor postear el contenido de tu archivo /etc/network/interfaces? 
Eso nos puede ayudar a ayudarte.

---

### Post by sebastian kraus on 2009-09-17
y eso donde esta :(

---

### Post by Hei Ku on 2009-09-17
Abris el Nautilus o explorador de archivos de tu eleccion, y vas a la carpeta /etc/network, y le das click al archivo interfaces.
Si no podés hacer esto, te pido que por favor le solicites ayuda a alguien que esté en condiciones de hacerlo, porque los pasos siguientes son más complicados y va a ser muy dificil que los realices sin al menos una destreza basica.

---

### Post by josecuervo86 on 2009-09-17
Estando en ubuntu: Anda a **Aplicaciones > Accesorios > Terminal**

Cuando se abre la terminal tipea:
```
gedit /etc/network/interfaces
```
Pone la **password** y apreta **Enter** (ojo que no vas a ver que esta escribiendose, pero se escribe igual, solo que no te la muestra)

Se va a abrir un editor de texto con info dentro. **Copia todo lo que haya** y **pegalo aca**.

---

### Post by sebastian kraus on 2009-09-17
auto lo
iface lo inet loopback
eso es lo q dice

---

### Post by Hei Ku on 2009-09-17
Agregá esto al final de ese archivo:

auto eth0
iface eth0 inet dhcp

Grabá.

En una terminal escribí:

sudo /etc/init.d/networking restart

Postea el resultado de ejecutar eso.

---

### Post by sebastian kraus on 2009-09-17
* Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
et0: ERROR while getting interface flags: No such device
et0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up et0.

---

### Post by pablo.s on 2009-09-17
Chequeá que estás
escribiendo en el archivo
et0 en lugar de eth0

---

### Post by sebastian kraus on 2009-09-17
* Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:d8:71:7f:b5
Sending on   LPF/eth0/00:11:d8:71:7f:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Hei Ku on 2009-09-17
Entonces el XP no tiene el DHCP activado.

Podes pasar la configuracion de red de XP?

Creo que abriendo una ventana de DOS y poniendo ipconfig te tira la informacion.

---

### Post by sebastian kraus on 2009-09-17
Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrador>ipconfig

Configuración IP de Windows


Adaptador PPP Arnet  - Conexión ADSL               :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 190.224.59.32
        Máscara de subred . . . . . . . . : 255.255.255.255
        Puerta de enlace predeterminada   : 190.224.59.32

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS :
        Dirección IP de autoconfiguración : 169.254.24.157
        Máscara de subred . . . . . . . . : 255.255.0.0
        Puerta de enlace predeterminada   :

C:\Documents and Settings\Administrador>

---

### Post by Hei Ku on 2009-09-17
Eso quiere decir que en XP tampoco tenés la red configurada.

---

### Post by sebastian kraus on 2009-09-18
entonces ahora la config de la pc con linux ya esta  y tengo q buscar como se configura la otra no?

---

### Post by andres2420 on 2009-09-19
Lo que tenes que hacer es simple.

Anda a windows y entra al Panel de control.Ahi anda Conexiones de red y despues ahi en el icono que dice "Conexion de Area Local" ( ES LA CONEXION QUE REPRESENTA LA PLACA DE RED y es donde esta conectado el cable cruzado) hace boton derecho propiedades.AHora en la solapa General, hacele doble click a "Protocolo Internet TCP/IP" y en la ventana que te aparece tilda la opcion que dice "Usar la siguiente direccion ip".En el campo direccion IP pone 192.168.1.1 y en el campo Mascara de sub red pone 255.255.255.0 y todo lo demas dejalo en blanco como esta y salva todos los cambios.

Ahora, como tenes un modem usb entonces tenes un icono para conectarte.Hacele boton derecho y anda a propiedades.Ahi busca la solapa "Opciones abanzada" y tilda "permitir a usuarios de otras redes conectarse a trabes de la conexion a internet de este equipo".Aplica todos los cambios

La explicasion de esto es simple.Primero configurar las placa de red tuya para que sea un puente entre la pc con ubuntu e internet ( provista por tu modem usb) y despues a ese marcador que usas es que cuando lo conectes, compartas esa conexion hacia la pc con ubuntu.

AHora anda a ubuntu y en la consola escribi esto

```
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0
```

AHora ponemos el puente que es lo que a vos te da internet ( la direccion 192.168.1.1)

```
 sudo route add default gw 192.168.1.1 dev eth0
```

Con esos 2 comandos configuras la placa de red con direccion ip/mascara de subred/puerta de enlace.

COn eso en teoria tendria que andar todo bien.

Cualquier cosa decime porque yo tube algo parecido a lo tuyo hace mucho y nunca un drama

Andrés

---

### Post by sebastian kraus on 2009-09-19
hola hice todo lo que vos habias escrito , el problema es q sigo sin internet en la de linux y en las conexiones de red que aparecen arriva a la derecha me aparece como desconectada..... q hago?

---

### Post by Hei Ku on 2009-09-19
Estas seguro que es un cable cruzado y no uno comun?

---

### Post by sebastian kraus on 2009-09-19
si ademas en la pc con win xp me aparece como conectado la concexion

---

### Post by Hei Ku on 2009-09-19
cual conexion? Porque en el XP tenes dos y una no estaba configurada?

Podes volver a poner ipconfig en el XP y ver q sale?

---

### Post by sebastian kraus on 2009-09-19
Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrador>ipconfig

Configuración IP de Windows


Adaptador PPP Arnet  - Conexión ADSL               :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 190.137.207.123
        Máscara de subred . . . . . . . . : 255.255.255.255
        Puerta de enlace predeterminada   : 190.137.207.123

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 192.168.1.1
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   :

C:\Documents and Settings\Administrador>

C:\Documents and Settings\Administrador>

C:\Documents and Settings\Administrador>

---

### Post by guillermolisi on 2009-09-19
> **sebastian kraus said:**
> Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrador>ipconfig

Configuración IP de Windows


Adaptador PPP Arnet  - Conexión ADSL               :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 190.137.207.123
        Máscara de subred . . . . . . . . : [COLOR=Red]255.255.255.255[/COLOR]
        Puerta de enlace predeterminada   : 190.137.207.123

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 192.168.1.1
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   :

C:\Documents and Settings\Administrador>

C:\Documents and Settings\Administrador>

C:\Documents and Settings\Administrador>
Es mascara marcada en rojo me parece que esta mal, deberia ser 255.255.255.0 a menos que esa instalacion de ADSL requiera de algo particular.

---

### Post by sebastian kraus on 2009-09-19
entonces q hago?

---

### Post by andres2420 on 2009-09-19
NO amigo, esa mascara esta bien...fijate bien que es la direccion ip publica de arnet.Vos sebastian no lo podes tocar ni nada...te la da arnet.

Seguramente tenes el modem usb el huawei mt810.Mira yo tube hace mucho como te dije algo muy parecido a lo tuyo.

Olvidate en primer lugar que desde windows en teoria tenes todo ok.
El problema ahora radida en que en la pc con ubuntu te aparece desconectado por lo que habria que ver:
[LIST]primero el cable ( pero mas raro es que te diga conectado desde el propio windows)..fijate como te dijeron que sea uno cruzado ( hace probar en una casa de electorinca o comunicasines con un tester para eso...es simple y no te tendrian que cobrar nada o 5 mangos...)
[/LIST]
[LIST]
dejando de lado el problem fisco, fijate de que este levantada la placa de red tirando un ifconfig y pegate el resultado aca,
te tendria que salir esto mira( es lo que vos al principio pusiste pero modificado por mi con lo que te dije)```
eth0 Link encap:Ethernet direcciónHW 00:11:d8:71:7f:b5 
inet dirección:**192.168.1.2** Difusión:**192.168.1.255** Máscara:255.255.255.0
dirección inet6: fe80::211:d8ff:fe71:7fb5/64 Alcance:Vínculo
ARRIBA DIFUSIÓN CORRIENDO MULTICAST MTU:1500 Métrica:1
RX packets:91 errors:0 dropped:0 overruns:0 frame:0
TX packets:357 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:13786 (13.7 KB) TX bytes:98844 (98.8 KB)
Interrupción:23 Dirección base: 0x4000
```[/LIST]
[LIST]proba si no tirando abajo la placa de red y levantandola con ifconfig eth0 down y despues ifconfig eth0 up ( anteponiendo el sudo en lo 2 comandos)[/LIST]
[LIST]otra cosa mas es que lo trataria si por comandos no podes o no resulta, hacelo entonces via grafica.Que vercion tenes de ubnutu?[/LIST]

Bueno por ahora no se me ocurre nada...un saludo pero quedate tranqui que lo que queres hacer anda y anda muy bien.

---

### Post by guillermolisi on 2009-09-19
andres2420, tenes razon, para la IP publica la mascara de subred debe estar totalmente cerrada.
Gracias por la observacion.

---

### Post by sebastian kraus on 2009-09-20
eth0      Link encap:Ethernet  direcciÃ³nHW 00:11:d8:71:7f:b5  
          direcciÃ³n inet6: fe80::211:d8ff:fe71:7fb5/64 Alcance:VÃ*nculo
          ARRIBA DIFUSIÃ“N CORRIENDO MULTICAST  MTU:1500  MÃ©trica:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:17292 (17.2 KB)  TX bytes:9095 (9.0 KB)
          InterrupciÃ³n:23 DirecciÃ³n base: 0x4000 

eth0:avahi Link encap:Ethernet  direcciÃ³nHW 00:11:d8:71:7f:b5  
          inet direcciÃ³n:169.254.8.154  DifusiÃ³n:169.254.255.255  MÃ¡scara:255.255.0.0
          ARRIBA DIFUSIÃ“N CORRIENDO MULTICAST  MTU:1500  MÃ©trica:1
          InterrupciÃ³n:23 DirecciÃ³n base: 0x4000 

lo        Link encap:Bucle local  
          inet direcciÃ³n:127.0.0.1  MÃ¡scara:255.0.0.0
          direcciÃ³n inet6: ::1/128 Alcance:AnfitriÃ³n
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  MÃ©trica:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1812 (1.8 KB)  TX bytes:1812 (1.8 KB)


eso es lo q dice tengo instalado el ultimo creo el 9.04

---

### Post by Hei Ku on 2009-09-20
En una terminal poné:

sudo gedit /etc/network/interfaces


Y en el archivo ese poné esto para eth0

```

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1


```

guardá, salí y reiniciá la interfaz.

---

### Post by sebastian kraus on 2009-09-20
no nada ...... sigo sin internet ... :S :( el iconito de la red en ubuntu sige como desconectado .....

---

### Post by andres2420 on 2009-09-20
Y todo lo demas que te dije?

Hace las cosas via grafica.Primero boton derecho al icono y anda a "Editar la conexiones" y ahi en la ventana andate a la solapa "Cableada".
Ahi te tendria que salir una que sea eth0 y si la seleccionas te aparece al lado tre boton.Anda a "Editar".Ahi tilda la opcion "Conectar automaticamente" y ahora andate a la solapa ultima "Ajustes IPV4".
Donde dice "Metodo" ahi elegi **Manual** y despues hace un click en "Añadir" y vas a ahi te deja el espacio en blanco para que bajo la columna "Direccion" pongas 192.168.1.2 despues hace un click al lado pero bajo la columna "mascara de subred" y pone 255.255.255.0 y despues en "puerta de enlace" pone 192.168.1.1 y ya que estas en "sevidores dns" pone 192.168.1.1 ( esto es para que esta maquina le pregunte a la puerta de enlace las direcciones...o sea esta maquina le pregunte a la otra de win xp y la de win xp con su salida a internet obtenga los datos).Aplica todos lo cambios y te tendria que decir conectado.

Me pone en duda esa tercer conexion llamada ** eth0:avahi** que es la misma ( tiene la misma MAC) pero tiene una APIPA ( porque el servidor dhcp de win xp no esta por eso se asigna una direccion la conexion misma).FIjate si en la solapa Cableada te aparecen esas 2 (eth0 y eth0:avahi), elimina la ultima dejando solo eth0 y configurala como te dije en el parrafo anterior.

---

