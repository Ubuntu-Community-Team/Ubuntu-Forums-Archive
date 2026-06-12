---
title: "Conky 1.7.2 no muestra la interface de red correcta"
date: 2009-10-03
forum: Software
---

### Post by Bruce M. on 2009-10-03
> **Mustaine666 said:**
> tengo un problema.. no me andan los graficos de la coneccion de internet! .. 

```

TEXT
eth-1
   ${font Sans:size=9:weight=bold} ${color #FF0000}  NET: (${addr eth1}) ${hr 2} $font
   ${color #FF0000}Up: ${color }${upspeed eth1} k/b
   ${upspeedgraph eth1 25,140 206900 3bc300}
   ${color #FF0000}Down: ${color }${downspeed eth1}k/b${color}
   ${downspeedgraph eth1 25,140 f1d900 d01800}
   ${color #FF0000} Upload: ${color}   $alignr${totalup eth1}
   ${color #FF0000} Download: ${color}    $alignr${totaldown eth1}

eth-0
   ${font Sans:size=9:weight=bold} ${color #FF0000}  NET: (${addr eth0}) ${hr 2} $font
   ${color #FF0000}Up: ${color }${upspeed eth0} k/b
   ${upspeedgraph eth0 25,140 206900 3bc300}
   ${color #FF0000}Down: ${color }${downspeed eth0}k/b${color}
   ${downspeedgraph eth0 25,140 f1d900 d01800}
   ${color #FF0000} Upload: ${color}   $alignr${totalup eth0}
   ${color #FF0000} Download: ${color}    $alignr${totaldown eth0}

```

Are you sure you connect with eth1?
¿Estas seguro que conecta con eth1?

Pruebe 0 y 1

Bruce

---

### Post by Bruce M. on 2009-10-03
Conky v1.7.1 y/o Conky v1.7.2: [GetDeb]("http://www.getdeb.net/app.php?name=gnome%20subtitles") o directamente a [Conky]("http://www.getdeb.net/search.php?keywords=conky")!

Que tengas un buen día
Bruce

---

### Post by Mustaine666 on 2009-10-04
> **Bruce M. said:**
> Are you sure you connect with eth1?
¿Estas seguro que conecta con eth1?

Pruebe 0 y 1

Bruce


ahora pruebo.. pero me dice q la conexion es eth1

---

### Post by Mustaine666 on 2009-10-04
> **Bruce M. said:**
> Conky v1.7.1 y/o Conky v1.7.2: [GetDeb]("http://www.getdeb.net/app.php?name=gnome%20subtitles") o directamente a [Conky]("http://www.getdeb.net/search.php?keywords=conky")!

Que tengas un buen día
Bruce

te comento.. baje el archivo .deb de conky v1.7.2 .. y cuando pongo 
sudo dpkg -i [nombre del archivo] 

me sale esto

```
mustaine@mustaine-desktop:~/Escritorio$ sudo dpkg -i conky_1.7.2-1~getdeb1_i386.deb
(Leyendo la base de datos ...  
153557 ficheros y directorios instalados actualmente.)
Preparando para reemplazar conky 1.7.2-1~getdeb1 (usando conky_1.7.2-1~getdeb1_i386.deb) ...
Desempaquetando el reemplazo de conky ...
dpkg: problemas de dependencias impiden la configuración de conky:
 conky depende de libimlib2; sin embargo:
  El paquete `libimlib2' no está instalado.
 conky depende de liblua5.1-0; sin embargo:
  El paquete `liblua5.1-0' no está instalado.
dpkg: error al procesar conky (--install):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para man-db ...
Se encontraron errores al procesar:
 conky

```hay alguna solucion?:confused:

---

### Post by guillermolisi on 2009-10-04
Si, podes usar el Gdebi Package Installer que resuelve estas cuestiones de dependencias cuando va a instalar el paquete .deb

Gdebi esta en los repositorios de Ubuntu.

---

### Post by Mustaine666 on 2009-10-04
lo arregle con la consola.. como superusuario.. 

con "sudo apt-get -f install" . y se arreglaron las dos dependencias!

---

### Post by guillermolisi on 2009-10-04
> **Mustaine666 said:**
> lo arregle con la consola.. como superusuario.. 

con "sudo apt-get -f install" . y se arreglaron las dos dependencias!
Eso es una instalacion forzada y no siempre es recomendable hacerla sin saber cuales podrian ser sus consecuencias ya que podrias haber reemplazado alguna libreria en lugar de otra que no es la adecuada para otras funciones/programas que tenes en tu sistema.

---

### Post by Mustaine666 on 2009-10-04
> **guillermolisi said:**
> Eso es una instalacion forzada y no siempre es recomendable hacerla sin saber cuales podrian ser sus consecuencias ya que podrias haber reemplazado alguna libreria en lugar de otra que no es la adecuada para otras funciones/programas que tenes en tu sistema.


ahh que buen dato.. ahora estoy por instalarlo al Gdebi Package Installer .. 
muchas gracias por el dato! .. 


siguiendo con el tema del conky y los graficos de red.. les traigo una foto 

[[IMG]http://a.imagehost.org/t/0805/asd_3.jpg[/IMG]]("http://a.imagehost.org/view/0805/asd_3") 

ese es la conexion con el conkyrc .. 

y este es el resultado
[[IMG]http://a.imagehost.org/t/0891/proba.jpg[/IMG]]("http://a.imagehost.org/view/0891/proba") ..

cual puede ser la solucion.. cambie todos los valores para todos los lados posibles... pero no puedo hacerlo andar!

---

### Post by jjgomera on 2009-10-04
bueno, estas seguro de haber subido-descargado algo en la sesión, no?

que te devuelve la orden **sudo ifconfig**

---

### Post by Mustaine666 on 2009-10-04
> **jjgomera said:**
> bueno, estas seguro de haber subido-descargado algo en la sesión, no?

que te devuelve la orden **sudo ifconfig**

```

eth0      Link encap:Ethernet  direcciónHW 00:0c:6e:c5:1d:64  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Dirección base: 0xb000 

eth1      Link encap:Ethernet  direcciónHW 00:1c:a2:3a:36:75  
          Direc. inet:10.0.0.10  Difus.:10.0.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21c:a2ff:fe3a:3675/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

```

aviso q estuve bajando.. varias cosas.. navegando.. osea use internet!

---

### Post by Mustaine666 on 2009-10-14
bueno.. todavia no pude hacer que ande.. asi q les muestro otra cosa q encontre!.. 

[[img]http://i.imagehost.org/t/0613/Sin_nombre.jpg[/img]](http://i.imagehost.org/view/0613/Sin_nombre)

[[img]http://i.imagehost.org/t/0804/conky.jpg[/img]](http://i.imagehost.org/view/0804/conky)

resultado del ifconfig

```
eth0      Link encap:Ethernet  direcciónHW 00:0c:6e:c5:1d:64  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Dirección base: 0xb000 

eth1      Link encap:Ethernet  direcciónHW 00:1c:a2:3a:36:75  
          Direc. inet:10.0.0.10  Difus.:10.0.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::21c:a2ff:fe3a:3675/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

```

uso la coneccion eth1 .. me parece muy raro que no ande.. ya q descargo navego.. y sigue quedando en 0 .. que se puede hacer?

---

### Post by Mustaine666 on 2009-10-14
algun administrador puede cerrar esto.. ya esta solucionado

---

### Post by guillermolisi on 2009-10-14
> **Mustaine666 said:**
> algun administrador puede cerrar esto.. ya esta solucionado
Como fue solucionado ?

---

### Post by Mustaine666 on 2009-10-14
lo que pasa es q estaba usando el modem con cable usb.. y lo conecte por ethernet .. y le asigne el usuario contraseña y la conexion eth0 ..

y ahora funciona perfecto.. y hasta mejoro la conexion a internet!. 

muchas gracias a todos por sus ayudas

---

### Post by 3nG3ndR0 on 2009-10-15
hola tienes funcionando concky 1.7.2 a mi no me muestra ni el calendario ni la red aquí esta mi detalle [http://ubuntuforums.org/showthread.php?t=1290375](http://ubuntuforums.org/showthread.php?t=1290375)

---

