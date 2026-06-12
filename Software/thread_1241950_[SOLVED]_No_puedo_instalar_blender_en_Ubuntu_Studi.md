---
title: "[SOLVED] No puedo instalar blender en Ubuntu Studio 9.04"
date: 2009-08-16
forum: Software
---

### Post by cordaxter2.0 on 2009-08-16
Hola. He buscado en google algo al respecto pero no encuentro nada.
Resulta que actualicé de 8.10 a 9.04, y a partir de aquí no pude abrir blender (lo tenía en el escritorio). Voy a synaptic y veo que no está instalado. Cuando intento instalarlo me sale lo siguiente:
 [B]"No se pudiero marcar todos los paquetes para la instalación.
Los siguientes paquetes tienen dependencias no resolubles. Asegúrese de que están añadidos y activados todos los repositorios necesarios en las preferencias.[/B]
 [B]blender:
 Depende: libavcodec52 pero no va a ser instalado o
     libavcodec-unstripped-52 pero no va a ser instalado"
[/B]
 Luego busqué esas dependencias e intenté marcarlas y me salio:
[B]
"¿marcar los cambios adicionales requeridos?
La acción afecta a otros paquetes. Los cambios siguientes se requieren para proceder."[/B]
 ...y me mostró una lista de 21 paquetes entre los que se encontraban codecs, aplicaciones (cinelerra, k9copy, openmovie editor, etc.) ademas del paquete ubuntustudio-video. 
 Como ya he dicho, no he encontrado ninguna solución en la web.
Si alguien me puede ayudar se lo agradezco.

---

### Post by Hei Ku on 2009-08-16
Podes poner esto en una terminal y copiar el resultado?

sudo apt-get install blender

---

### Post by pablo.s on 2009-08-16
Dos cuestiones:

1. A Blender lo instalaba del repositorio
main o era de un PPA?
2. Esos 21 paquetes los quiere actualizar
o desinstalar?

---

### Post by cordaxter2.0 on 2009-08-17
Esto es lo que me sale:

	 	 	 	 	  usuario@ubuntu:~$ sudo apt-get install blender 
 [sudo] password for usuario:  
 Leyendo lista de paquetes... Hecho 
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho 
 No se pudieron instalar algunos paquetes. Esto puede significar que 
 usted pidió una situación imposible o, si está usando la distribución 
 inestable, que algunos paquetes necesarios no han sido creados o han 
 sido movidos fuera de Incoming. 
 La siguiente información puede ayudar a resolver la situación: 
  
 Los siguientes paquetes tienen dependencias incumplidas: 
   blender: Depende: libavcodec52 (>= 3:0.svn20090128-1) pero no va a instalarse o 
                     libavcodec-unstripped-52 (>= 3:0.svn20090128-1) pero no va a instalarse 
 E: Paquetes rotos 
 usuario@ubuntu:~$ 



Yo lo hice con synaptic e intenté instalar dicha dependencia. A partir de allí es que me pedía **desinstalar **los paquetes relacionados con el video.
En cuanto a lo del repositorio main o ppa, al ser nuevo en esto, no sabría que decirte, supongo que del repositorio main. 

Gracias por la ayuda, espero sus respuestas.

---

### Post by Hei Ku on 2009-08-17
Que te aparece si pones?

sudo apt-get install libavcodec52

---

### Post by sianhulo on 2009-08-17
> **cordaxter2.0 said:**
> Esto es lo que me sale:

                          usuario@ubuntu:~$ sudo apt-get install blender 
 [sudo] password for usuario:  
 Leyendo lista de paquetes... Hecho 
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho 
 No se pudieron instalar algunos paquetes. Esto puede significar que 
 usted pidió una situación imposible o, si está usando la distribución 
 inestable, que algunos paquetes necesarios no han sido creados o han 
 sido movidos fuera de Incoming. 
 La siguiente información puede ayudar a resolver la situación: 
  
 Los siguientes paquetes tienen dependencias incumplidas: 
   blender: Depende: libavcodec52 (>= 3:0.svn20090128-1) pero no va a instalarse o 
                     libavcodec-unstripped-52 (>= 3:0.svn20090128-1) pero no va a instalarse 
 [SIZE=4][COLOR=Red]E: Paquetes rotos [/COLOR][/SIZE]
 usuario@ubuntu:~$ 



Yo lo hice con synaptic e intenté instalar dicha dependencia. A partir de allí es que me pedía **desinstalar **los paquetes relacionados con el video.
En cuanto a lo del repositorio main o ppa, al ser nuevo en esto, no sabría que decirte, supongo que del repositorio main. 

Gracias por la ayuda, espero sus respuestas.

ve a sypnatic,repara los paquetes rotos(te sale en la barra de herramientas),e intenta volver a instalar el blender.

---

### Post by cordaxter2.0 on 2009-08-18
Esto es lo que me sale:

	 	 	 	 	  usuario@ubuntu:~$ sudo apt-get install libavcodec52 
 [sudo] password for usuario:  
 Leyendo lista de paquetes... Hecho 
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho 
 No se pudieron instalar algunos paquetes. Esto puede significar que 
 usted pidió una situación imposible o, si está usando la distribución 
 inestable, que algunos paquetes necesarios no han sido creados o han 
 sido movidos fuera de Incoming. 
 La siguiente información puede ayudar a resolver la situación: 
  
 Los siguientes paquetes tienen dependencias incumplidas: 
   libavcodec52: Depende: libavutil49 (< 3:0.svn20090303-99) pero 3:20080706-0.3lenny1 va a ser instalado o 
                          libavutil-unstripped-49 (< 3:0.svn20090303-99) pero no va a instalarse 
 E: Paquetes rotos 
 usuario@ubuntu:~$ 



En cuanto a los paquetes rotos. No sé muy bien como es. Lo que vi, es que tengo instalado y en estado "local u obsoleto" el paquete libavcodec51. Yo intenté darle a la opción **reparar paquetes rotos, **tanto seleccionando ese paquete como sin seleccionar ninguno. Lo que synaptic hace es pestañear su interface y nada más.
Otro dato que puede servir de algo es que tengo a blender en estado "no instalado(configuración residual).


De nuevo gracias

---

### Post by pablo.s on 2009-08-18
Postea tu archivo sources.list
que se encuentra en /etc/apt.
Creo que tu problema es que
no se han generado bien los
repositorios de Jaunty.

---

### Post by cordaxter2.0 on 2009-08-18
supongo que te referís a esto, en pricipio se me abría el programa origenes del software, después lo abrí en modo de texto:  	 	 	 	 	  # added by the release upgrader deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe # deb [http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/](http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/) stable main # (desactivado en la actualización a jaunty) ## Medibuntu - Ubuntu 7.10 "gutsy gibbon" # deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free # (desactivado en la actualización a jaunty) # deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe  # deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to # newer versions of the distribution.  # deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted  ## Major bug fix updates produced after the final release of the ## distribution. deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team, and may not be under a free licence. Please satisfy yourself as to ## your rights to use the software. Also, please note that software in ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse  ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. # deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse # deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. This software is not part of Ubuntu, but is ## offered by Canonical and the respective vendors as a service to Ubuntu ## users. # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner  # Line commented out by installer because it failed to verify: # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted # Line commented out by installer because it failed to verify: # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted # Line commented out by installer because it failed to verify: # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe # Line commented out by installer because it failed to verify: # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe # Line commented out by installer because it failed to verify: # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse # Line commented out by installer because it failed to verify: # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse #Jahshaka # deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) /binary-i386/ # (desactivado en la actualización a jaunty)

---

### Post by pablo.s on 2009-08-18
Por lo que puedo descifrar
(el formato es muy confuso)
están bien los repositorios,
con un detalle que me resulta
un poco extraño:
Estas utilizando el mirror de
España? Prueba cambiandolos
a un mirror mas cercano, como
Brasil y actualiza. Luego prueba
si te instala Blender.

---

### Post by cordaxter2.0 on 2009-08-18
no se que paso con el formato.  A ver si ahora sale bien. Lo de españa es porque vivo en españa aunque soy uruguayo.

# added by the release upgrader
deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
# deb [http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/](http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/) stable main # (desactivado en la actualización a jaunty)
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free # (desactivado en la actualización a jaunty)
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
#Jahshaka
# deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) /binary-i386/ # (desactivado en la actualización a jaunty)

---

### Post by pablo.s on 2009-08-18
[COLOR=Red]# added by the release upgrader
deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
# deb [http://ftp.eq.uc.pt/software/unix/Li...an-multimedia/]("http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/") stable main # (desactivado en la actualización a jaunty)
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free # (desactivado en la actualización a jaunty)
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (2008102:cool:]/ intrepid main multiverse restricted universe[/COLOR]

[COLOR=Red]# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (2008102:cool:]/ intrepid main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.[/COLOR]

[COLOR=Black][COLOR=Red]# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (2008102:cool:]/ intrepid main multiverse restricted universe[/COLOR]
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
[/COLOR] 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

[COLOR=Red]## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse[/COLOR]

[COLOR=Red]## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner[/COLOR]

[COLOR=Red]# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
#Jahshaka
# deb [http://repo.jahshaka.org/ubuntu/dapper](http://repo.jahshaka.org/ubuntu/dapper) /binary-i386/ # (desactivado en la actualización a jaunty)


[COLOR=Black]Borrá todo lo que marqué en rojo
y recargá los repositorios.[/COLOR]
    [/COLOR]

---

### Post by cordaxter2.0 on 2009-08-18
ok! lo haré y luego te cuento, ya que me tengo que ir a laburar y el modem 3g este es demasiado lento. 
gracias...

---

### Post by cordaxter2.0 on 2009-08-19
Borré lo que estaba en rojo, recargué e intenté de nuevo. El resultado es el mismo:

usuario@ubuntu:~$ sudo apt-get install blender
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  blender: Depende: libavcodec52 (>= 3:0.svn20090128-1) pero no va a instalarse o
                    libavcodec-unstripped-52 (>= 3:0.svn20090128-1) pero no va a instalarse
E: Paquetes rotos
usuario@ubuntu:~$ sudo apt-get install libavcodec52
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  libavcodec52: Depende: libavutil49 (< 3:0.svn20090303-99) pero 3:20080706-0.3lenny1 va a ser instalado o
                         libavutil-unstripped-49 (< 3:0.svn20090303-99) pero no va a instalarse
E: Paquetes rotos

---

### Post by pablo.s on 2009-08-19
Probá con [este paquete]("http://www.getdeb.net/release/4659").

---

### Post by cordaxter2.0 on 2009-08-20
bajé el paquete de blender y me puso: [COLOR=Red]Error: No se puede instalar 'libavcodec52'[/COLOR]
[COLOR=Black]El problema es ese paquete[/COLOR], lo raro es que tengo instalado el libavcodec51.
Estoy entre formatear e instalar todo de nuevo, o dejar que me desinstale todos los archivos que me pida, instalar blender y luego volver a instalar todo lo demás (si me deja). Si no, no me queda otra que usarlo en xp.

---

### Post by cordaxter2.0 on 2009-08-20
A ver si esto ayuda:

busqué en el archivo var/lib/dpkg/status y no encontré ningún paquete roto (broken)

Esta es la lista de archivos:

**Cinelerracv-gl**
 **dvgrab**
 **ffmpeg2theora**
 **gem**
 **gstreamer0,10-ffmpeg**
 **gstreamer0,10-plugins-bad-multiverse**
 **k9copy**
 **libavdevice52**
 **libmjpegtools-1,9**
 **libmjpegtools0c2a**
 **libpostproc51**
 **libquicktime1**
 **libwscale0**
 **libsynfig0**
 **libsynfigapp0**
 **mjpegtools**
 **openmovieeditor**
 **pytube**
 **synfigstudio**
 **ubuntustudio-video**

---

### Post by pablo.s on 2009-08-20
Supongo que vas a tener que 
desinstalarlos nomás, dado que
son paquetes que fueron instalados
mediante repositorios que tenías en
Intrepid y ahora quedaron huerfanos.

Los paquetes de Cinelerra y Open
Movie Editor creo que están en el
[repositorio de Akirad]("http://akiradproject.net/repository") y los demás en
universe y/o multiverse de Jaunty se
encuentran.

Disculpá desde ya que no tengamos
una solución mejor.

---

### Post by jjgomera on 2009-08-20
tienes que resolver ese paquete roto antes de continuar, eliminalo:
```

sudo aptitude update
sudo aptitude purge libavutil49 libavutil-unstripped-49 libavcodec52
sudo aptitude install blender
```

---

### Post by cordaxter2.0 on 2009-08-20
**Antes quiero saber si dándole a aceptar no me quedo sin gnome.** [B]Esto es lo que me sale:

[/B]
sudo aptitude purge libavutil49 libavutil-unstripped-49 libavcodec52
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Los siguientes paquetes están ROTOS:
  ffmpeg ffmpeg2theora gstreamer0.10-ffmpeg libavcodec51 libavdevice52 
  libavformat52 libpostproc51 libswscale0 libsynfig0 openmovieeditor 
Se ELIMINARÁN los siguientes paquetes:
  libavutil49{p} libmjpegtools0c2a{u} libx264-59{u} 
0 paquetes actualizados, 0 nuevos instalados, 3 para eliminar y 68 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 1380kB.
No se satisfacen las dependencias de los siguientes paquetes:
  openmovieeditor: Depende: libavutil49 (>= 3:0.svn20080206-8) pero no es instalable o
                            libavutil-unstripped-49 (>= 3:0.svn20080206-8) pero no es instalable
  libswscale0: Depende: libavutil49 (>= 3:20080706) pero no es instalable
  libpostproc51: Depende: libavutil49 (>= 3:20080706) pero no es instalable
  libavformat52: Depende: libavutil49 (>= 3:20080706) pero no es instalable
  gstreamer0.10-ffmpeg: Depende: libavutil49 (>= 3:0.svn20080206-8) pero no es instalable o
                                 libavutil-unstripped-49 (>= 3:0.svn20080206-8) pero no es instalable
  ffmpeg2theora: Depende: libavutil49 (>= 3:0.svn20080206-8) pero no es instalable o
                          libavutil-unstripped-49 (>= 3:0.svn20080206-8) pero no es instalable
  libsynfig0: Depende: libavutil49 (>= 3:0.svn20080206-8) pero no es instalable o
                       libavutil-unstripped-49 (>= 3:0.svn20080206-8) pero no es instalable
  ffmpeg: Depende: libavutil49 (>= 3:20080706) pero no es instalable
  libavcodec51: Depende: libavutil49 (>= 3:20080706) pero no es instalable
  libavdevice52: Depende: libavutil49 (>= 3:20080706) pero no es instalable
Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
cinelerracv-gl
dvgrab
ffmpeg
ffmpeg2theora
gem
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad-multiverse
k9copy
libavcodec51
libavdevice52
libavformat52
libmjpegtools-1.9
libpostproc51
libquicktime1
libswscale0
libsynfig0
libsynfigapp0
mjpegtools
openmovieeditor
pytube
synfigstudio
ubuntustudio-video

Dejar las siguientes dependencias sin resolver:
kino recomienda ffmpeg
audacity recomienda libavformat52 | libavformat-unstripped-52
puredata recomienda gem
stopmotion recomienda dvgrab
stopmotion recomienda ffmpeg
ubuntu-restricted-extras recomienda gstreamer0.10-plugins-bad-multiverse
ubuntu-restricted-extras recomienda gstreamer0.10-ffmpeg
La puntuación es -904

¿Acepta esta solución? [Y/n/q/?] y
Se ELIMINARÁN los siguientes paquetes:
  cinelerracv-gl{a} dvdauthor{u} dvgrab{a} ffmpeg{a} ffmpeg2theora{a} gem{a} gstreamer0.10-ffmpeg{a} gstreamer0.10-plugins-bad-multiverse{a} k9copy{a} libavcodec51{a} libavdevice52{a} libavformat52{a} libavutil49{p} 
  libboost-regex1.34.1{u} libebml0{u} libguicastcv-gl{u} liblzo2-2{u} libmatroska0{u} libmjpegtools-1.9{a} libmjpegtools0c2a{u} libmpeg3cv-gl{u} libpostproc51{a} libquicktime1{a} libquicktimecv-gl{u} libswscale0{a} libsynfig0{a} 
  libsynfigapp0{a} libx264-59{u} mencoder{u} mjpegtools{a} mkvtoolnix{u} openmovieeditor{a} optlibx11-noxcb-6{u} optlibx11-noxcb-data{u} pytube{a} synfigstudio{a} twolame{u} ubuntustudio-video{a} vamps{u} 
0 paquetes actualizados, 0 nuevos instalados, 39 para eliminar y 62 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 84,5MB.
¿Quiere continuar? [Y/n/?]

---

### Post by pablo.s on 2009-08-20
Si, eliminalos.

---

### Post by cordaxter2.0 on 2009-08-20
ok! desinstaló eso y ahora instala blender. Tengo el paquete que descargué pero prefiero hacerlo desde synaptic (por estabilidad). Luego me encargaré de instalar el resto. 

gracias y seguiré en los foros. Espero que para la proxima para ayudar... je

---

### Post by pablo.s on 2009-08-20
En este momento estoy compilando
la versión diaria de Blender 2.50.
Saludos.

---

### Post by cordaxter2.0 on 2009-08-21
mmm. veo que sabes del tema. 
bueno, suerte y gracias

---

