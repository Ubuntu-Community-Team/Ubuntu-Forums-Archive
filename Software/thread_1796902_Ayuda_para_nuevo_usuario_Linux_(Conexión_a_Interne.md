---
title: "Ayuda para nuevo usuario Linux (Conexión a Internet)"
date: 2011-07-04
forum: Software
---

### Post by 53RG10 on 2011-07-04
Hola a todos
Empecé con Linux hace unas semanas y no le encontré la vuelta al siguiente problema:
Tengo el modem Arescom NDS1060USB y vi algunas manera de configurar lo conexión pero no me puedo conectar.
Tengo Ubuntu 11.04 "Natty Narhwal", que me lo reconoce al módem, porque parpadea el led del llink y se conecta, pero no entiendo cómo tengo que hacer para conectarme a mi proveedor, que es Telefónica por un lado (me cobra la línea) y Netizen por otro (proveedor de internet). ¿Hay alguna especie de programa o paquete para conectarse a internet? Porque en Windows sólo creo la cuenta con el asistente y listo.
Muchas gracias y cualquier cosa que no haya aclarado pregunten.
Saludos

---

### Post by juancarlospaco on 2011-07-04
No tiene para conectar por RJ-45 UTP (la fichita que parece como de telefono pero mas grande) ...?

---

### Post by 53RG10 on 2011-07-04
No, tiene la entrada de cable de línea de teléfono y la otra es la ficha USB que va a la PC.

---

### Post by gmunioz on 2011-07-06
Prueba lo siguiente:
Baja estos archivos:
[http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz](http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz)
[http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz)

Instala estos paquetes
build-essential, linux-headers-`uname -r` libatm1

Instala el driver nuevo
En consola, dentro del directorio donde se descargaron los archivos ueagle

sudo su
tar xzf ueagle-atm-1.3.tar.gz
cd ueagle-atm-1.3
make
make install
cd ..
tar xzf ueagle-data-1.1.tar.gz
cd ueagle-data-1.1
mkdir /lib/firmware/ueagle-atm
cp -a * /lib/firmware/ueagle-atm
modprobe ueagle-atm

=====================================

Crea un archivo llamado ueagle-atm en la ruta /etc/ppp/peers 
gedit /etc/ppp/peers/ueagle-atm
Pon este contenido:

user "tu_nombre_de_usuario"
plugin pppoatm.so 8.32
noipdefault
usepeerdns
defaultroute
persist
noauth

Modifica el archivo /etc/ppp/chap-secrets
gedit /etc/ppp/chap-secrets 

Debe tener una linea simple como esta
"tu_nombre_de_usuario"  "*"  "tu_clave"  "*" 

Una vez terminado al ejecutar
modprobe pppoatm
pon ueagle-atm 
ifconfig 

Deberia aparecer algo asi como:

ppp0    Link encap:Point-to-Point Protocol  
inet addr:83.30.157.107  P-t-P:213.25.2.202  Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
RX packets:2019 errors:0 dropped:0 overruns:0 frame:0
TX packets:2025 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3 
RX bytes:724078 (707.1 KiB)  TX bytes:184065 (179.7 KiB)

Dado que comentas que el modem aparece como reconocido,
prueba simplemente crear los archivos sin instalar los drivers es decir en principio solo desde esta linea hacia abajo:
=====================================================

si no funciona asi instala los drivers.

---

### Post by andy_91 on 2011-07-06
Hasta donde yo se los modem usb no eran compatibles con ubuntu, pero seguro que de gusty hasta ahora algo debe haber cambiado

---

### Post by 53RG10 on 2011-07-06
OK, gracias
Voy a probar cuando me vuelva internet (estoy desde ayer sin internet: ¡¡¡Gracias Speedy!!!). Me había instalado justo antes de que me lo corten el LinuxMint (Espero que no se enojen por probar otro...) y ahí había podido hacerlo andar, voy a ver si puedo en Ubuntu, que si no me equivoco el Mint está basado en Ubuntu, ¿no?
Muchas gracias
Saludos

---

### Post by 53RG10 on 2011-07-12
[SIZE=2]Bueno, al final lo solucioné de la siguiente manera:[/SIZE]

[I]# br2684ctl -b -c 0 -a 8.35
br2684ctl[3826]: Interface "nas0" created sucessfully
br2684ctl[3826]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[3826]: Interface configured

# pppoeconf
Plugin rp-pppoe.so loaded.

 Now, you can make a DSL connection with "pon dsl-provider" and terminate it with "poff".

 The DSL connection has been triggered. You can use the "plog" command to see the status or "ifconfig ppp0" for general interface info.
[/I]
[SIZE=2]Gracias de todas maneras, y aprovechándome hago otra pregunta: ¿Se puede hacer un "conector a internet automático" para no tener que hacer eso cada vez? Como si fuera un .exe en Windows.

Gracias nuevamente
Saludos[/SIZE]

---

