---
title: "No puedo conectarme a internet!"
date: 2010-06-16
forum: Software
---

### Post by Belitus on 2010-06-16
Hola a todos Primero que nada tengo Ubuntu 10.04.. quiza esta duda ya la tengan resuelta porque creo que algo lei referido a ella pero la verdad es que no entendi nada :S
la duda es porque la primera vez configure el modem con el pppoeconf y me pude conectar a internet pero cuendo le prendi reinicie o lo que fuere no me deja conectarme y esto es lo poco que se que quiza pueda resultar de ayuda!
esto es lo ultimo que hice (cuando inicio secion y abro consola):
[B]
belito@blackstar:~$ sudo pppoeconf
[/B] 
NO CONECTADO
Lo siento, se consultaron 1 interface, pero no respondió el concentrador de acceso de su proveedor.
Por favor, verifique sus cables de red y del módem. Otra razón del fallo puede ser también que esté
ejecutándose otro proceso pppoe y que éste esté controlando el módem.
<Aceptar>

"Hasta ahi lo entendi porque antes ya la habia configurado"

lo que me parece raro es que tengo ip:

**belito@blackstar:~$ ifconfig ppp0**

Link encap:Protocolo punto a punto Direc. [SIZE=3][COLOR=Lime]**inet:186.59.36.91**[/COLOR][/SIZE] P-t-P:200.63.148.79 Másc:255.255.255.255
ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST MTU:1492 Métrica:1
Paquetes RX:33 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:33 errores:0 perdidos:0 overruns:0 carrier:0 colisiones:0 long.colaTX:3
Bytes RX:1616 (1.6 KB) TX bytes:1500 (1.5 KB)

"y lo que puse tambien fue para "activarlo" o eso es lo que lei por uno de estos foros"

belito@blackstar:~$ sudo pon dsl-provider

Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5


[CENTER][SIZE=3] pero sigo sin poder navegar!!
[/SIZE][/CENTER]
 

La verdad es que soy re nuevo en linux y de suerte que ser re pocos comandos (esos 3 y uno que otro mas :P )
Tampoco se como borrar y volver a cargar los datos del pppoeconf (asi por lo menos lo configuro cada vez que la encienda)
Alguien me podria dar una facil solucion, me refiero a facil que sea entendible por alguien con tan poco conocimiento
Ademas alguna critica del posteo porque la verdad no se como se pregunta entre linuxeros

---

### Post by atari130xe on 2010-06-20
Hola como estàs yo harìa lo siguiente para evitarte muchos problemas y agilizar la conexion: Modem en modo router, entràs al set up de tu moen por medio del navegador de internet seguis los pasos que seguro estaran en algun lado en la net y listo, chau problemas, serìa interesante que postees el nombre y modelo de tu modem (claro siempre y cuando sea ADSL). saludos):P

PD: en el sitio de Telefònica tenès como rutear los modems ADSL que ellos entregan y supongo que en el sitio de Telecom serà igual.

---

### Post by kornykyano on 2010-06-20
Por lo que entiendo el modem ya esta configurado. Entonces para conectarte cada vez que reinicies es hacer un script o escribir en la terminal lo siguiente:

1- Cargar los modulos
```
sudo modprobe ueagle-atm
sudo modprobe br2684
```
2- Segun tu proveedor de internet:
a) Cargar configuracion de Arnet 
```
sudo br2684ctl -c 0 -b -a 0.33
```
b) Cargar configuracion de Speedy 
```
sudo br2684ctl -c 8 -b -a 0.85
```
3- Conexión USB
```
sudo ifconfig nas0 up
```
4- Iniciar conexion
```
sudo pon dsl-provider
```

Espero que te sea útil.

---

