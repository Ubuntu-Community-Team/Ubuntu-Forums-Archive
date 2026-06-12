---
title: "Problema con compartición de carpetas Ubuntu/Ubuntu"
date: 2009-09-20
forum: Software
---

### Post by donmatas on 2009-09-20
Estimad@s:

tengo dos equipos portátiles en casa, uno de los cuales es mi "media center". Quiero habilitar la compartición de carpetas he hice lo lógico. Botón derecho, compartir carpeta, instalar el "servicio", reiniciar, activar compartición con los permisos adecuados. Lo hice en las dos máquinas. El problema es que al ir a Lugares/Red, sólo encuentro una "Red de Windows" y al pincharla aparece un "WORKGROUP" lo pincho y sólo aparece mi equipo y sus carpetas compartidas y no el otro al que quiero acceder. Aveces también pasa que dice que "falló al obtener la lista de compartición del servidor ubuntu".

He navegado buscando soluciones, pero todas están orientadas a resolver la compartición con Win$ y no ubuntu/ubuntu

Uso 9.04

gracias de antemano
DM

---

### Post by Carlos C on 2009-09-21
Hola. Moví tu hilo al subforo "software". Por favor recuerda publicar en el subforo adecuado, cuando tengas dudas puedes leer el [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") publicado en cada uno, en donde se especifica lo que corresponde publicar en ellos.

En caso de dudas te recomiendo leer [aquí]("http://ubuntuforums.org/showthread.php?t=1162750").


Respecto a tu problema, creo que te serviría mirar acá:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html)

Saludos.

---

### Post by donmatas on 2009-09-21
gracias carlos!
le daré un vistazo al link y te cuento. 
tendré ojo con donde posteo

saludos
DM

---

### Post by moreback on 2009-09-22
Buena la guía, Carlos_C, la apliqué acá en la oficina y todo parece funcionar correctamente.

---

### Post by _ZeTa on 2009-09-22
> **donmatas said:**
> gracias carlos!
le daré un vistazo al link y te cuento. 
tendré ojo con donde posteo

saludos
DM

bueno bueno, y como te fue con las comparticiones? :confused::popcorn:

---

### Post by donmatas on 2009-09-22
> **_ZeTa said:**
> bueno bueno, y como te fue con las comparticiones? :confused::popcorn:

la verdad es que no he probado la solución propuesta por tres razones:

1. Está orientada a compartir carpetas con *windows* lo cual no es mi caso.

2. una vez me funcionó el asunto de compartir carpetas entre ubuntus sin hacer más que instalar el servicio y compartir las carpetas y reiniciar.

3. el punto N° 7 del tutorial resulta intimidante. Dice: "7. Comparte los directorios que desees. La manera de compartir en Hardy/Intrepid y en Gutsy son diferentes". Yo tengo Jaunty

si alguien tiene instrucciones más específicas agradeceré

saludos
DM

---

### Post by Carlos C on 2009-09-22
> **donmatas said:**
> 
"7. Comparte los directorios que desees. La manera de compartir en Hardy/Intrepid y en Gutsy son diferentes". Yo tengo Jaunty


con Jaunty se puede compartir usando el mismo método que con Intrepid y Hardy. Yo también tengo Jaunty y lo hago del mismo modo.
Respecto a compartir, de qué modo quieres hacerlo? pensé que querías usar Samba, por eso la guía.

---

### Post by donmatas on 2009-09-22
> **Carlos C said:**
> con Jaunty se puede compartir usando el mismo método que con Intrepid y Hardy. Yo también tengo Jaunty y lo hago del mismo modo.
Respecto a compartir, de qué modo quieres hacerlo? pensé que querías usar Samba, por eso la guía.

con samba también. Lo tengo instalado, pero el tema es uqe la otra vez que lo hice (con los mismos computadores y SO) y no necesité hacer nada más que instalar samba (cuando compartes carpeta por primera vez te ofrece "instalar el servicio" que es justamente samba"). Lo que no entiendo es porqué tengo que modificar scripts ahora, si estoy compartiendo carpetas entre computadores con jaunty...

saludos
DM

---

### Post by Carlos C on 2009-09-23
No es necesario modificar ningún script, es cosa de que verifiques algunos elementos básicos, como el nombre del grupo de trabajo, los permisos, los usuarios, la sintaxis del archivo de configuración, etc. En realidad no debiera ser tan complejo, está todos ahí, pero si prefieres hacerlo de otro modo puede que alguien más te pueda ayudar.

Saludos.

---

### Post by donmatas on 2009-09-23
gracias
veré si el fin de semana me animo

salud
DM

---

### Post by asterix77 on 2009-09-24
Si ambos PC usan Ubuntu ¿No sería mejor usar NFS?, tengo entendido que es más rápido por ser para redes linux-linux.

---

### Post by donmatas on 2009-09-24
> **asterix77 said:**
> Si ambos PC usan Ubuntu ¿No sería mejor usar NFS?, tengo entendido que es más rápido por ser para redes linux-linux.

como es eso de NFS?

saludos
DM

---

### Post by asterix77 on 2009-09-24
Samba es un protocolo de red para intercambiar archivos entre pc con linux y windows. También se puede usar (creo), entre pc con linux con el inconveniente de que es un poco más lento en intercambiar archivos.

[http://es.wikipedia.org/wiki/Samba_(programa](http://es.wikipedia.org/wiki/Samba_(programa))

NFS (Network File System) hace lo mismo en general, pero en entornos unix-linux.

[http://es.wikipedia.org/wiki/NFS](http://es.wikipedia.org/wiki/NFS)


Saludos

---

### Post by donmatas on 2009-09-26
Hoy prendí los dos compus y chachan! la red está funcionand ¿cómo? ni idea, pues yo no hice nada...

adjunto pantallazos para los incrédulos

salud
DM

---

### Post by moreback on 2009-09-26
A mí, por algún motivo que desconozco, me empezó a negar la autenticación en todos los pcs con Ubuntu que instalé en la oficina.

Voy a ver en la semana si sigue el problema.

---

### Post by donmatas on 2009-11-21
> **donmatas said:**
> Hoy prendí los dos compus y chachan! la red está funcionand ¿cómo? ni idea, pues yo no hice nada...

adjunto pantallazos para los incrédulos

salud
DM

Estimad@s;

tal como esta cuestión se solucionó, dejo de funcionar. Es realmente extraño. Ahora pasé ambos computadores (instalación limpia) a Karmic porque soporta mejor su tarjeta de video y sonido. La situación es la siguiente:

PC1 (dell 6400 con Ubuntu Karmic): parece funcionar bien. Al compartir una carpeta, esta aparece en "Red". Sin embargo no puedo ver el PC2 ni sus carpetas compartidas. El problema parece estar en el otro computador.

PC2 (dell 1545 con Ubuntu Karmic): voy a red y no aparece nada más que "red de windows" si pincho en ella me lanza el típico error "no se pudo montar el lugar. Falló al obtener la lista de compartición del servidor". Cuando comparto una carpeta, todo parece normal, pero al reiniciar ya no está compartida. 

Seguí las orientaciones sugeridas por Carlos C que están [aquí]("http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html"). Las apliqué en el PC2 y ahora voy a red y sólo aparece "red de windows" pero al pincharla al menos me muestra un "WORKGROUP" y al pincharlo me muestra las carpetas compartidas de PC2. Intuyo que el problema es que NTF no está funcionando...agradezco cualquier orientación

saludos
DM

---

### Post by Carlos C on 2009-11-21
Qué ocurre cuando en ambos computadores corres el comando:
```
smbclient -L <nombre del equipo> -Uusuario_samba
```
para ver qué recursos están compartidos para ese usuario. Lo mismo si escribes:
```
smbclient -L <nombre del equipo> -U%
```
para ver lo que un usuario no autentificado vería. Lo digo porque entiendo que ninguno de los dos computadores es capaz de ver al otro.

Saludos.

---

### Post by donmatas on 2010-02-13
> **Carlos C said:**
> Qué ocurre cuando en ambos computadores corres el comando:
```
smbclient -L <nombre del equipo> -Uusuario_samba
```
para ver qué recursos están compartidos para ese usuario. Lo mismo si escribes:
```
smbclient -L <nombre del equipo> -U%
```
para ver lo que un usuario no autentificado vería. Lo digo porque entiendo que ninguno de los dos computadores es capaz de ver al otro.

Saludos.

Compa:

disculpe el tiempo que me tomó hacer la prueba, pero aquí van los resultados:

**EN EL DELL 1545 CON KARMIC KOALA**
```
@el-libertario:~$ smbclient -L EL-LIBERTARIO -matias
Unrecognised protocol level atias
Enter matias's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Vídeos         Disk      
	IPC$            IPC       IPC Service (el-libertario server (Samba, Ubuntu))
	la escafandra y la mariposa Disk      
	la escafandra y la mariposa [dvd-rip] [spanish] [[www.divxatope.com]](www.divxatope.com]) Disk      
	música docta   Disk      
	schubert for two Disk      
	24 season 2     Disk      
	la constitucion es como el pico_data Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	EL-LIBERTARIO        el-libertario server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            EL-LIBERTARIO
```

**EN EL DELL 6400 CON KARMIC KOALA**

```
@LyM:~$ smbclient -L LYM -U%
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (LyM server (Samba, Ubuntu))
	vídeos         Disk      
	música         Disk      
	soda stereo     Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	LYM                  LyM server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            LYM

```

Agregar que ahora en los dos computadores al ingresar a "Red" me aparece el respectivo computador y "Red de Windows". En el primero encuentro las carpetas compartidas por el mismo. En el segundo aparece el "WORKGROUP" y si lo pincho aparece el propio computador nuevamente

Eso sería

muchas gracias por la ayuda

DM

---

### Post by moreback on 2010-02-13
Me parece que funcionaría mejor si tuvieras los dos equipos en el mismo grupo de trabajo.

---

### Post by Carlos C on 2010-02-14
> **moreback said:**
> Me parece que funcionaría mejor si tuvieras los dos equipos en el mismo grupo de trabajo.
Si, verifica que el grupo de trabajo sea el mismo:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html)

Saludos.

---

### Post by donmatas on 2010-02-15
> **Carlos C said:**
> Si, verifica que el grupo de trabajo sea el mismo:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html)

Saludos.

Gracias, lo intentaré cuando tenga un rato y les cuento como me fue. En todo caso, mirando lo que postié justo antes pareciera que los dos tienen el mismo grupo de trabajo ("WORKGROUP")

dm

---

### Post by donmatas on 2010-02-15
> **Carlos C said:**
> Si, verifica que el grupo de trabajo sea el mismo:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-cambiar-el-grupo-de-trabajo-en.html)

Saludos.

Tal como sospechaba, el grupo de trabajo es el mismo. Ejecuté sudo gedit /etc/samba/smb.conf en ambos compus:

**DELL 1545 CON UBUNTU 9.10**

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


```

**DELL 6400**

Estrañalmente apareció el siguiente mensaje en la terminal al abrir el archivo con gedit:

```
Falló en GConf: Falló al contactar con el servidor de configuraciones; algunas de las posibles causas son que necesite activar TCP/IP en ORBit, o que tiene bloqueos de NFS debidos a una caída de sistema. Consulte http://www.gnome.org/projects/gconf/ para más información. (Detalles -  1: No se pudo enviar un mensaje al demonio de GConf: Message did not receive a reply (timeout by message bus))
```

En todo caso el resultado es el mismo, pues de todos modos se abrio el smb.conf

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
```

Creo que el mensaje extraño pudo ser producido porque ejecuté el comando desde el Dell 1545 mediante la aplicación de "escritorio remoto", pues ahora que lo hago limpio desde el Dell 6400 no aparece el mensaje.


saludos
DM

---

### Post by Carlos C on 2010-02-16
con "ifconfig" anota el ip de cada computador y trata de acceder a ellos con nautilus. Puede que tengas problemas con los nombres de los equipos pero sí puedas compartir carpetas utilizando el ip local.

---

### Post by moreback on 2010-02-16
Aparte de que los equipos estén en el mismo grupo de trabajo, también debieran estar en el mismo segmento de red, ya que el protocolo SMB utiliza el broadcast para ubicar a resto de los equipos.

Saludos.

---

### Post by donmatas on 2010-02-16
> **moreback said:**
> Aparte de que los equipos estén en el mismo grupo de trabajo, también debieran estar en el mismo segmento de red, ya que el protocolo SMB utiliza el broadcast para ubicar a resto de los equipos.

Saludos.

eso qué significa en la práctica 
ojo que soy un usuario sin conocimientos en redes

saludos
DM

---

### Post by donmatas on 2010-02-16
> **Carlos C said:**
> con "ifconfig" anota el ip de cada computador y trata de acceder a ellos con nautilus. Puede que tengas problemas con los nombres de los equipos pero sí puedas compartir carpetas utilizando el ip local.
con nautilus?
cómo hago eso?

saludos
DM

---

