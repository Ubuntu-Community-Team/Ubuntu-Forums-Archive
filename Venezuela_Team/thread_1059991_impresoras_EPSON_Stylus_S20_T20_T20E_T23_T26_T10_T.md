---
title: "impresoras EPSON Stylus S20 T20 T20E T23 T26 T10 T11"
date: 2009-02-04
forum: Venezuela Team
---

### Post by JunCTionS on 2009-02-04
A petición de un compañero hispanohablante, esta es la guía traducida de la instalación de las [_impresoras EPSON Stylus S20 T20 T20E T23 T26 T10 T11]("http://ubuntuforums.org/showthread.php?t=964784") empezada por el usuario_ [ c_c ]("http://ubuntuforums.org/member.php?u=411282")


3.0.1 [_Descarga el archivo .deb de acá_]("http://rapidshare.com/files/167463640/pips.tar.gz.html")
3.0.2 Descomprimelos con 'tar -xvf pips.tar.gz' o el programa de tu escogencia (como Ark si usas kubuntu)

3. Instala los drivers con el comando: 'sudo dpkg -i ./pips-*.deb'
4. Obtienes unos mensajes (ignoralos ^_^)
5. edita el siguiente archivo, escribiendo en el terminal (o consola): 'sudo vim /etc/init.d/ekpd'
6. Copia el siguiente texto (para pegar en Konsole, se presiona Shift+Ins)
```

# Photo Image Print System
# Copyright (C) 2002-2005 EPSON AVASYS Corporation.
# Copyright (C) SEIKO EPSON CORPORATION 2002-2005.
#
# . /etc/rc.d/init.d/functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/EPAva/core/ekpd
NAME=ekpd
PIDFILE=/var/run/$NAME.pid
DESC="EPSON Avasys printing daemon"

unset TMPDIR

test -f $DAEMON || exit 0

OLDMASK=`umask`
umask 000

case "$1" in
start)
pidlist=`pidof $NAME`
if [ "x" = "x$pidlist" ]; then
echo -n "Starting $NAME:"
start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON
fi
;;

stop)
echo -n "Stopping ekpd:"
start-stop-daemon --stop --retry 5 --name $NAME
;;

restart)
$0 stop
sleep 2
$0 start
;;

*)
echo "Usage: ekpd { start | stop | restart }" >&2
exit 1
;;
esac

umask $OLDMASK
exit 0

```

6.a. Esto no me parece evidente: Presiona Esc, y luego escribe ':w' (sin comillas) y luego':q' 
7.Vuelve el archivo ejecutable corriendo el comando: 'sudo chmod +x /etc/init.d/ekpd'
8. Instalar unas cuantas librerías con el comando 'sudo apt-get install libtiff4 libpng3' (Gracias a [_swudee_]("http://ubuntuforums.org/member.php?u=230945") por actualizar esta línea)
9. Hacer un vínculo a este archivo con este comando 'sudo ln -s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3'
10. Y copia el archivo de configuración de ekpd: 'sudo cp /usr/local/EPAva/printer/st20/ekpdrc_st20 /etc/ekpdrc'
11. Corre'sudo ekpd-tool' para verificar que los parámetros están correctos
Printer Name : st<El nombre de tu impresora, por ejemplo 20 en mi caso que tengo una T20>
Connection Method : <USB>
Device Path : lp0
Activar la casilla de 'Default Printer' si esta será la impresora predeterminada
12. Iniciar el ekpd: 'sudo /etc/init.d/ekpd start'
Acá yo obtuve el siguiente error
 /etc/init.d/ekpd: 2: to: not found
 Starting ekpd
El cual ignoré sin problemas

13. Abre Firefox (o Konqueror) y escribe 'localhost:631' en la barra de direcciones
14. Selecciona 'Administration', y luego 'Add Printer'
15. Ponle un nombre (name), ubicación (location) y descripción (description) cualquiera
16. Selecciona 'Epson Stylus Txx USB #1' del menú desplegable
17. Selecciona 'Epson Stylus Txx Photo Image Print System (en)' como el modelo
18. Si quieres envia una página de prueba a la impresora o simplemente imprime lo que necesites. La página de prueba me pareción bastante repleta de colores, así que si estás tacaño como yo en la tinta mejor no imprimas la de prueba ;).

---

### Post by morelosuno on 2009-02-21
Gracias. Si funciona

Por fin mi impresora funciona en ubuntu. Es lo que me faltaba para cambiarme definitivamente a Linux.

---

