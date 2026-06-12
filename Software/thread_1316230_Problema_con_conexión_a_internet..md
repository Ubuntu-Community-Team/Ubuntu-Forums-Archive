---
title: "Problema con conexión a internet."
date: 2009-11-05
forum: Software
---

### Post by fezh on 2009-11-05
Principalmente hay que tomar en cuenta que yo soy bastante nuevo en esto de Ubuntu. Para probar medianamente sus capacidades me descargué el [Wubi]("http://wubi-installer.org/").
Ahora, el problema parece estar en Ubuntu en sí. La verdad es que no tengo la menor idea de como conectarme a internet.
Por si puede llegar a ser útil, tengo banda ancha Speedy 3mb y un módem un poco viejito (SpeedTouch 330). Por otra parte la versión de Ubuntu que me bajé desde Wubi es la 9.10 para AMD64.

---

### Post by juancarlospaco on 2009-11-05
Conectalo por la placa de red y sale andando.

Si no tiene para placa de red (es como una ficha de telefono pero mas grande) avisanos.

---

### Post by fezh on 2009-11-05
> **juancarlospaco said:**
> Conectalo por la placa de red y sale andando.

Si no tiene para placa de red (es como una ficha de telefono pero mas grande) avisanos.De hardware entiendo poco y nada. Voy a tratar de interpretar lo que dijiste y si no puedo aviso.

EDIT: No, no pude. Se ve que mi PC no tiene placa de red. ¿Que más puedo hacer al respecto?

---

### Post by juancarlospaco on 2009-11-05
Por donde se conecta (fisicamente) tu PC? por USB?

---

### Post by deafters on 2009-11-06
hola to tengo el speedtouch330 usb, si tenes el mismo entra aquí y bajate el archivo este: [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)
luego copialo a tu home y descomprimilo ( todo eso podes hacerlo desde la interfaz gráfica como para no liarte) una vez descomprimido te va a crear una carpeta en tu home identificable con el speedtouch330, entras allí y vas a encontrar un archivo que se llama instalar.sh, hace boton derecho del mouse sobre ese archivo y vas a propieades, después a permisos y allí marcas donde dice permitir ejecutar el archivo como un programa aceptas y ya esta listo para se ejecutado.
Entonces le haces doble clik a instalar.sh y se te va a abrir una ventana preguntan que queres hacer y le decis ejecutar en una terminal, se te va a abrir una consola donde si seguís los pasos tenes todo andando.
si algo falla o no funciona avisame que lo seguimos , suerte

---

### Post by fezh on 2009-11-06
> **deafters said:**
> hola to tengo el speedtouch330 usb, si tenes el mismo entra aquí y bajate el archivo este: [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)
luego copialo a tu home y descomprimilo ( todo eso podes hacerlo desde la interfaz gráfica como para no liarte) una vez descomprimido te va a crear una carpeta en tu home identificable con el speedtouch330, entras allí y vas a encontrar un archivo que se llama instalar.sh, hace boton derecho del mouse sobre ese archivo y vas a propieades, después a permisos y allí marcas donde dice permitir ejecutar el archivo como un programa aceptas y ya esta listo para se ejecutado.
Entonces le haces doble clik a instalar.sh y se te va a abrir una ventana preguntan que queres hacer y le decis ejecutar en una terminal, se te va a abrir una consola donde si seguís los pasos tenes todo andando.
si algo falla o no funciona avisame que lo seguimos , suerteSi, tengo ese módem. Ahora, acerca de lo que escribiste, no me funcionó. También seguí la guía detallada [acá]("http://steve-parker.org/speedtouchconf/") pero tampoco conseguí nada.
Me parece que el problema está cuando quiero ejecutar algo desde una terminal, por que se me abre la consola pero se me cierra en un segundo o menos :/

---

### Post by josecuervo86 on 2009-11-06
Fezh, hace esto, abri una terminal y movete mediante el comando **cd** hasta el directorio (carpeta) donde esta el archivo **instalar.sh**. Una vez en el directorio escribi:

```
sh instalar.sh
```

Y le das [Enter]. Si va todo bien se va a instalar, si hay algun error te lo va a decir. En caso de que pase esto ultimo copialo (al error) y pegalo aca.

Te doy un ejemplo de como hacerlo, ya que sos nuevo:

Supongamos que yo baje el archivo en la carpeta /home/josecuervo86/Downloads y lo descomprimi ahi mismo creando se una carpeta llamada SpeedTouch dentro de esta ultima con el archivo instalar.sh dentro de ella. Entonces ese archivo estaria en: /home/josecuervo86/Downloads/SpeedTouch

Hasta ahi bien? bueno, entonces agarras, abris una terminal y pones esto:

```
cd Downloads/SpeedTouch
``` y le das [Enter] (fijate que no hace falta que pongas /home/josecuervo86 antes de poner el resto ya que la terminal cuando abre lo hace en tu carpeta). Una vez hecho esto pones:

```
sh instalar.sh
```

y listo.

Te hago una aclaración mas, donde yo puse josecuervo86 vos tenes que poner tu nombre de usuario porque lo hice a modo de ejemplo ;)

Creéme qu es mucho mas dificil explicarlo que hacerlo :)

---

### Post by fezh on 2009-11-07
Gracias, pero en su momento cuando lo intenté me aparecía que el archivo no existía (install-sh.sh, no lo tengo en castellano).
En mi intento de conectarme a internet desde Ubuntu seguí la guía que se incluye con el código source, pero falle en el que yo creo es el último paso, make install, ya que me dice que lo tengo que ejecutar desde root, y no tengo la menor idea de lo que me esta hablando.

EDIT: Al final pude usar el comando make install con el sudo. El problema que tengo ahora es que no me puedo conectar a internet (que novedad..) por que me esta faltando un archivo en /etc/speedtouch/, pero no me deja tocar esa carpeta por que me dice que no tengo privilegios suficientes (y eso que estoy con la cuenta de administrador).

---

### Post by josecuervo86 on 2009-11-07
Fezh, podrias mostrarnos exactamente que dice el mansaje?

Para modificar archivos o carpetas dentro del sistema de archivos base necesitas tener privilegios. Una forma fácil de acceder con privilegios es escribir en terminal:

```
sudo nautilus
```

Esto te abre un navegador de archivos con privilegios. Pero **ojo**, no toques nada si no sabes bien que estas haciendo!

Seria bueno que primero nos muestres el error para asi poder ver que hace falta hacer

---

### Post by fezh on 2009-11-07
Sigo sin poder acceder a /etc/speedtouch..

Por otra parte ahora si les puedo mostrar lo que me falta:

```
administrador@ubuntu:~$ sudo speedtouch-setup
PPPD Configuration Script for GNU/Linux

You must accept the license on
http://www.speedtouch.com/driver_upgrade_lx_3.0.1.2.htm and download
the file SpeedTouch330_firmware_3012.zip.
Copy this file in the directory /etc/speedtouch.
```Y tengo la mala leche de no conseguir ese archivo por ningún lado >.>

---

### Post by josecuervo86 on 2009-11-07
Fezh, dale una leidita a esto: [http://preguntaslinux.org/howto-instalar-driver-modem-adsl-speedtouch-330-usb-t-543.html](http://preguntaslinux.org/howto-instalar-driver-modem-adsl-speedtouch-330-usb-t-543.html)

---

### Post by fezh on 2009-11-07
> **josecuervo86 said:**
> Fezh, dale una leidita a esto: [http://preguntaslinux.org/howto-instalar-driver-modem-adsl-speedtouch-330-usb-t-543.html](http://preguntaslinux.org/howto-instalar-driver-modem-adsl-speedtouch-330-usb-t-543.html)Gracias, con eso CASI me conecto a internet, miren lo que me mostró la terminal cuando hice todo lo detallado ahí:
```

administrador@ubuntu:~$ cd Descargas/speedtouchconf-27-Jun-2006
administrador@ubuntu:~/Descargas/speedtouchconf-27-Jun-2006$ sudo sh speedtouchconf.sh
[sudo] password for administrador: 

[: 715: unexpected operator
(c) Steve Parker, 17 Oct 2002 - 2005 (http://steve-parker.org)
speedtouchconf comes with ABSOLUTELY NO WARRANTY; for details type:
    speedtouchconf.sh -gpl
This is free software, and you are welcome to redistribute it
under certain conditions.
See the included file COPYING for more details.

************************************************
*                                              *
$*       speedtouchconf.sh by Steve Parker      *
*                                              *
*    http://speedtouchconf.sourceforge.net/    *
$* based on speedtouch.sourceforge.net project  *
*                                              *
************************************************

$If you have any problems with this script, mail me
$(steve at steve-parker dot org) with the files
$/tmp/speedtouch.txt and (possibly) /var/log/messages for diagnosis.
$The kernel speedtch module is loaded. This is not
$compatible with the speedtouch usermode driver.
$Removing the speedtch module
$  Linux kernel version 2.6 okay.
/home/administrador/Descargas/speedtouchconf-27-Jun-2006
[: 741: Illegal number: 
*******************************************
*                                         *
$*     Please select your ISP Settings     *
*                                         *
*******************************************

$  Country/ISP            VPI    VCI
  Belgium, ?              8     35
  Denmark, Orang          8     35
  France, Wanadoo         8     35
  France, ?               8     67
  Italy, ?                8     35
  Netherlands, ?          8     48
  Netherlands             0     35
  Poland (NeoStrada)      0     35
  UK, Any                 0     38
  Austria (AON)           8     48
  US, BellSouth           8     35
  Singapore Pacificnet    0    100
$Please type your VPI VCI numbers (eg, 0 38 for UK)
8 35
$Please enter your ISP Login ID (eg another@hg1.btinternet.com)
---------@speedy
$Please enter your ISP Password
------
$Settings: 
  VPI / VCI : 8 / 35
  Login     : -------@speedy
  Password  : -------
$Are these correct? (Y/N)
Y
$No further user interaction is required.
$Configuring SpeedTouch Driver...
$Software Configuration - SUCCESS
$Building SpeedTouch Driver...
$Software Build - SUCCESS
$Installing SpeedTouch Driver...
$Software Installation - SUCCESS
$Creating ppp files in /etc/ppp
$You can ignore any insmod hints here...
[: 747: UHCI: unexpected operator
[: 747: UHCI: unexpected operator
[: 747: UHCI: unexpected operator
[: 747: UHCI: unexpected operator

$   *** Configuration finished. Starting the connection ***

dom nov  8 21:53:24 ART 2009
$The modem lights should start flashing for approx. 60 seconds...
$You might see some messages about USBDEVFS_BULK failed - you can ignore this.
Nov  8 21:53:24 ubuntu modem_run[4441]: modem_run version 1.3.1 started by administrador uid 0
dom nov  8 21:55:00 ART 2009
$The lights should both be solid green now.
Nov  8 21:55:00 ubuntu modem_run[4441]: ADSL synchronization has been obtained
Nov  8 21:55:00 ubuntu modem_run[4441]: ADSL line is up (4832 kbit/s down | 608 kbit/s up)
$Running : /usr/sbin/pppd call adsl
$Called pppd - you should see some messages about IP addresses now...
Nov  8 21:55:10 ubuntu pppd[4454]: pppd 2.4.5 started by root, uid 0
Nov  8 21:55:10 ubuntu pppd[4454]: Using interface ppp0
Nov  8 21:55:10 ubuntu pppd[4454]: Connect: ppp0 <--> /dev/pts/1
sudo speedtouch-Nov  8 21:55:41 ubuntu pppd[4454]: LCP: timeout sending Config-Requests
Nov  8 21:55:41 ubuntu pppd[4454]: Connection terminated.
sNov  8 21:55:42 ubuntu pppd[4454]: Modem hangup
ppp0: error al obtener información sobre la interfaz: Dispositivo no encontrado
*********************************
$* Don't seem to have connected. *
*********************************
$Please check the username and password in /etc/ppp/*-secrets.
$Also check the VPI/VCI in /etc/ppp/peers/adsl
$Then run /etc/init.d/speedtouch start
$Current settings: ------@speedy / ------- / 8 / 35
```Los datos de la conexión los modifiqué para postearlos acá, pero me los tomó como válidos aparentemente.

---

### Post by guillermolisi on 2009-11-07
> $Please check the username and password in /etc/ppp/*-secrets.
$Also check the VPI/VCI in /etc/ppp/peers/adsl
[FONT=monospace]Ahi te esta pasando una punta de por donde podria venir el problema.
[/FONT]

---

### Post by josecuervo86 on 2009-11-07
Fijate qu en el mismo post dice que para telecom pueden ser VPI/VCI 0 33. Que ISP estas usando?

---

### Post by fezh on 2009-11-07
> **guillermolisi said:**
> [FONT=monospace]Ahi te esta pasando una punta de por donde podria venir el problema.
[/FONT]Si, ya había visto eso, pero como aclaré anteriormente no puedo ver/abrir/modificar los archivos dentro de /etc/

> **josecuervo86 said:**
> Fijate qu en el mismo post dice que para telecom pueden ser VPI/VCI 0 33. Que ISP estas usando?Ya lo había aclarado en el primer post, tengo Speedy 3mb.

---

### Post by josecuervo86 on 2009-11-07
Fezh, no lo habia visto, perdon. Te comento que en mi caso mi nombre de cuenta es ....@speedy**plus**, no solo speedy. Fijate si modificando eso conecta

---

### Post by fezh on 2009-11-07
> **josecuervo86 said:**
> Fezh, no lo habia visto, perdon. Te comento que en mi caso mi nombre de cuenta es ....@speedy**plus**, no solo speedy. Fijate si modificando eso conectaNop, acabo de probar desde Windows para no perder tiempo en reiniciar la máquina. Cuando le agrego el "plus" me aparece un mensaje tan copado como este cuando quiero entrar a alguna página:

```
Usted está accediendo a su conexión a Internet con un usuario y/o password erróneo el cual no corresponde a su cuenta.
Para poder seguir navegando ingrese con su usuario y password, si no lo recuerda haga click aquí.
```Te cuento que yo contraté el servicio hace más o menos 3 años, cuando todavía tenía mi querida Pentium II. Empecé con una conexión de 256kb y a medida que pasó el tiempo me fueron aumentando la velocidad sin cambiar mucho el precio.

PD: En ese momento mi cuenta era ...@speedy01, después quedó ...@speedy solo.

---

### Post by josecuervo86 on 2009-11-07
Ok, entonces pareciera que esta todo bien para conectarse. Revisaste los ficheros que te propone el script?

---

### Post by guillermolisi on 2009-11-07
> **fezh said:**
> Si, ya había visto eso, pero como aclaré anteriormente no puedo ver/abrir/modificar los archivos dentro de /etc/

Ese tema habria que investigarlo y solucionarlo cuanto antes. Asi no recomiendo seguir adelante con el sistema ya que en algun momento, como ha pasado recientemente, sera necesario ver/editar desde una terminal/consola algun archivo.
Abri otro thread en software para trabajar sobre ese problema.

---

### Post by Mauro22 on 2009-11-07
> > **josecuervo86 said:**
> Fijate qu en el mismo post dice que para telecom pueden ser VPI/VCI 0 33. Que ISP estas usando?

[QUOTE]Ya lo había aclarado en el primer post, tengo Speedy 3mb.[/QUOTE]

Estoy medio desenganchado del tema, pero él usa Speedy.... por lo tanto los valores son VPI 8 - VCI 35


Espero no quedar descolgado, pero no encontré esta respuesta.

---

### Post by josecuervo86 on 2009-11-07
Mauro, me respondio despues eso que pusiste, por lo tanto esta bien que usa 8/35 :)

---

### Post by Mauro22 on 2009-11-07
> **josecuervo86 said:**
> Mauro, me respondio despues eso que pusiste, por lo tanto esta bien que usa 8/35 :)

Me pasa por querer engancharme... ](*,) =D

---

### Post by deafters on 2009-11-08
> **fezh said:**
> Si, tengo ese módem. Ahora, acerca de lo que escribiste, no me funcionó. También seguí la guía detallada [acá]("http://steve-parker.org/speedtouchconf/") pero tampoco conseguí nada.
Me parece que el problema está cuando quiero ejecutar algo desde una terminal, por que se me abre la consola pero se me cierra en un segundo o menos :/

compañero me parece que antes que nada deberías ver el tema de el correcto funcionar de la consola.
te aseguro que yo no tuve problema alguno

---

### Post by guillermolisi on 2009-11-08
> **deafters said:**
> compañero me parece que antes que nada deberías ver el tema de el correcto funcionar de la consola.
te aseguro que yo no tuve problema alguno
Esta en curso ese tema en un thread aparte en la seccion Software.

---

