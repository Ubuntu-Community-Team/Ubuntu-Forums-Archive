---
title: "Como instalar VMware?"
date: 2008-08-27
forum: Software
---

### Post by victor_nesta on 2008-08-27
Antes de todo, ya busque en Google y en el foro. y ya tengo el VirtualBox.

Lo instale siguiendo la instrucciones de varios blogs que coincidían en el método.

Me apareció en aplicaciones/otros> VMware Server Console.
El tema es que se queda ¨iniciando¨ y se cierra.
No, se si me faltara algo, o me mande un moco en la instalación, (aunque lo instale 3 veces)

:confused::confused:

Gracias.

Ah me olvida.. En ubu Hardy

---

### Post by sergiom99 on 2008-08-27
Que queres instalar? VMWare Server, VMWare Workstation, VMWare Console?

Los dos primeros son para correr las maquinas virtuales, uno como servidor (y accedes con la consola) y el Workstation corres las virtuales en tu propia PC.
(Tambien esta el VM Player, que solo podes hacer andar una virtual ya creada, no podes crearla vos mismo)

Seguramente querras instalar la Workstation. Aca podes encontrar info sobre VMware:
[http://communities.vmware.com/](http://communities.vmware.com/)
[http://aprendizdetodo.wordpress.com/2006/11/27/instalar-vmware-workstation-en-ubuntu/](http://aprendizdetodo.wordpress.com/2006/11/27/instalar-vmware-workstation-en-ubuntu/)
[http://www.ubuntu-es.org/index.php?q=node/88899](http://www.ubuntu-es.org/index.php?q=node/88899)

suerte!

---

### Post by victor_nesta on 2008-08-29
Gracias por la respuesta!
Soy un Bolu entendí todo mal, creía que el server me aceptaba todo y que encima era gratis.
Bueh, instale el Workstation.

Seguí esta guía, [http://www.ubuntu-es.org/index.php?q=node/88899](http://www.ubuntu-es.org/index.php?q=node/88899)

todo bien, empiezan las preguntas, hasta llegar a esta:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

le doy enter y nada. Voy al directorio /usr/src/ y me fijo que hay, tengo 2 headers: /linux-headers-2.6.24-19 y /linux-headers-2.6.24-19-generic
 pruebo solo, con .../include/, con .../include/linux/, con /include/linux/version.h

y en todos me sale:
 is an existing directory, but it does not contain a "linux" subdirectory as expected.

o en algunos casos:
The path "/usr/src/linux-headers-2.6.24-19/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected.  
This can happen if the kernel has never been built, or if you have invoked the 
"make mrproper" command in your kernel directory.  In any case, you may want to
rebuild your kernel.

Según leí, algunos recompilaron el Kernel :confused::confused:, cosa que aun no me animo a tocar. 

¿Que puede estar pasando?
Gracias!!

---

### Post by victor_nesta on 2008-08-29
Perdón por el Doble, no fue mi intención hacer dump, me merezco la muerte!! 


SEGUNDO TIEMPO :KS:KS

Probe siguiendo estas instrucciones:
[http://www.ubuntu-es.org/index.php?q=node/5380](http://www.ubuntu-es.org/index.php?q=node/5380)

Bueno para solucionar esto debes de tener los headers,
yo lo pude arreglar de la siguiente manera.

$ sudo apt-get install linux-headers-`uname -r`

Después
Presionas desde la terminal

$ vmware

me dio un error en ingles señalandome la siguiente ruta lo cual hice esto:

$ sudo /usr/bin/vmware-config.pl

Desde este punto volvió a iniciar la instalacion, y en la parte que me daba el error entonces ya se resolvió

y El error ahora es Este:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-19-generic/include/

The directory of kernel headers (version 2.6.24.3) does not match your running 
kernel (version 2.6.24-19-generic).  Even if the module were to compile 
successfully, it would not load into the running kernel.


Por uno o por otro no funca.

Saludos

---

### Post by sergiom99 on 2008-08-29
proba con 
```
sudo apt-get install gcc gcc-c++ kernel-devel 
```

sino busca en los foros. la primerisima vez que instale vmware server (en un ubuntu server 6.06 que luego decidimos abandonar para volver a la linea CentOS) tuve un error parecido, que creo que lo arregle instalando esos paquetes, pero la solucion la encontre en los foros, de ubuntu y vmware.
suerte!

---

### Post by victor_nesta on 2008-08-29
Gracias por responder
Segun me cuenta ¨mi ubuntu¨ tengo instalados los últimos paquetes de ambos.
Mire y remire en foros y nada, seguiré. 

Comentario personal de nuevo usuario de ubuntu Linux:

Estas cosas me revientan las p****** 
Si Ubuntu (y Debian) es una de los GNU/Linux mas usados. ¿Por que caxo el equipo de WMware no saca un p*** paquete .deb para instalarlo sin mas?
¿Por que poro*** canonical no presiona un poco mas?
Si quisiera modificar las funcionalidades de tal o cual aplicación o del mismo OS, esta bien, hay que estudiar, tener conocimientos y posibles fallos/errores. Pero para correr un programa, tanta vuelta!!
Me re-caliento.
En fin Aguante Ubuntu y aguanten las aplicaciones fáciles de instalar, jeje
Seguiré investigando.
Gracias!!

---

### Post by Mister X on 2008-08-29
> **victor_nesta said:**
> Gracias por responder
Segun me cuenta ¨mi ubuntu¨ tengo instalados los últimos paquetes de ambos.
Mire y remire en foros y nada, seguiré. 

Comentario personal de nuevo usuario de ubuntu Linux:

Estas cosas me revientan las p****** 
Si Ubuntu (y Debian) es una de los GNU/Linux mas usados. ¿Por que caxo el equipo de WMware no saca un p*** paquete .deb para instalarlo sin mas?
¿Por que poro*** canonical no presiona un poco mas?
Si quisiera modificar las funcionalidades de tal o cual aplicación o del mismo OS, esta bien, hay que estudiar, tener conocimientos y posibles fallos/errores. Pero para correr un programa, tanta vuelta!!
Me re-caliento.
En fin Aguante Ubuntu y aguanten las aplicaciones fáciles de instalar, jeje
Seguiré investigando.
Gracias!!

hasta la version 7.10 lo podias instalar desde el repositorio oficial partner de ubuntu, ahora vmware dejó de ser partner de canonical...

---

### Post by sergiom99 on 2008-08-29
son 3:
gcc
gcc-c++
kernel-devel

ahh! para! ahora que lo vuelvo a mirar, el error dice
> The directory of kernel headers (version 2.6.24.3) does not match your running
kernel (version 2.6.24-19-generic).  o sea que los headers son != del kernel. no es que esta faltando como parecia al principio. habria que buscar por ese lado.

---

### Post by sergiom99 on 2008-08-29
esto lo vamos a hacer andar che:
proba con > Your current, running kernel is
$ uname -r
------
$ sudo apt-get update
$ sudo apt-get install build-essential
$ sudo aptitude install linux-headers-$(uname -r)
$ sudo aptitude install linux-headers-$(uname -r | sed 's/-[3-6]86$//')

Use --reinstall option if you must.
Y este otro mira todo lo que tiene que instalarle para poder hacerlo andar.
[http://www.howtoforge.org/forums/showthread.php?t=7306](http://www.howtoforge.org/forums/showthread.php?t=7306)

---

### Post by victor_nesta on 2008-08-30
Ah, a mi la 7.10 me duro instalada 1 semana como mucho!!
¿Por que dejo de ser partner de canonical? Aunque me puedo imaginar :mad: jeje

Muchas Gracias por las respuestas
A pesar de no superar lo de los Headers, tengo el player y el workstation en herramientas de sistema, pero cuando los ejecuto intenta cargarlos hasta que se cierran, como en el Server que cite al principio del post.

El link es para AMD/64 yo tengo i386 en 32b. 
¿Tengo que modificar esta linea: gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1? ¿todo? o ¿lo ejecuto igual y que pase lo que tenga que pasar?

---

### Post by Mister X on 2008-08-30
Igualmente creo que para intrepid van a sacar un paquete para automatizar la instalacion de varios componentes de vmware

[http://packages.ubuntu.com/intrepid/vmware-package](http://packages.ubuntu.com/intrepid/vmware-package)

---

