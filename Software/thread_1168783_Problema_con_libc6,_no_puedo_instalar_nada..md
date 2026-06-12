---
title: "Problema con libc6, no puedo instalar nada."
date: 2009-05-24
forum: Software
---

### Post by Hadso on 2009-05-24
Hola Gente. 
He bajado Fluxbuntu y lo he instalado en vieja PC. 
Estoy muy conforme con los resultados. El problema es que esta versión, por ser la que ofrece el sitio web oficial, está increiblemente desactualizada. 
Así que puse manos a la obra en actualizar el archivo sources.list.
Luego traté de instalar conky, dolphin, thunrar, etc. y no me lo permitía. 
Me mostraba un mensaje con una cantidad abismal de librerías para actualizar y demás. Con lo cual, lo dejé hacer su trabajo, pero siempre al finalizarlo dice que tiene un problema tratando de actualizar "libc6". 
Qué es lo que puedo hacer? Ya he buscado en el foro y he probado varios comandos que encontré. 

Por otro lado, seria posible que al tener desactualizadas las librerías del sistema no pueda ejecutar el Firefox 3.0 que bajé de su sitio oficial?
Dado que entro a la carpeta hago click en el archivo "firefox" (o lo llamo desde la consola) y no hace nada. Pareciera que el programa está por ejecutarse, pero al final no hace mas nada. Sería esto una consecuencia de no tener actualizadas las librerías?

Muchas gracias!!!

Hadso

---

### Post by Hei Ku on 2009-05-24
Por favor, pone los mensajes de error que te tira, para no hablar en el aire, sobre las miles de cosas que pudiste romper.

Tambien estaria bueno ver como te quedo el archivo sources.list, para saber contra que estas rompiendo.

PD: movido a Software

---

### Post by staar on 2009-05-24
bajaste fluxbuntu 7.10 ??? no era más fácil instalar desde el alternate un sistema básico de consola y después instalar fluxbox?

libc6 es la librería base del sistema, la usan casi todos los programas, ojo que podés romper todo...

como fue el procedimiento exacto que hiciste para actualizar?

saludos

---

### Post by guillermolisi on 2009-05-24
La version 7.10 aun esta soportada ?

Me parece que no por lo tanto no podra acceder a sus repositorios.

EDIT: Alternativa 1 - Probar de actualizar desde un CD mas moderno y con soporte y ver como evoluciona. Alternativa 2 - Llevar a cabo un fresh installation con una version soportada, por ejemplo enla forma sugerida antes desde un "alternate" agregandole despues Flux.

---

### Post by Hadso on 2009-05-25
Dado los comentarios que me hacen se me ocurre que sería mejor volver a instalar Fluxbuntu, ya sea el 7 o alguno posterior. Porque además, ni mucha data puedo darles sobre los errores que muestra la consola, porque no me permite compiar :@

¿Es aconsejable hacer esto?
¿Qué versión me recomiendan?
Una vez instalada, ¿qué comando tengo que tipear para actualizar el apt y no volver a tener problemas?

Estoy a la espectativa de cualquier otra seugerencia. 

Muchas gracias!!!!!

---

### Post by guillermolisi on 2009-05-25
> **Hadso said:**
> Dado los comentarios que me hacen se me ocurre que sería mejor volver a instalar Fluxbuntu, ya sea el 7 o alguno posterior. Porque además, ni mucha data puedo darles sobre los errores que muestra la consola, porque no me permite compiar :@

¿Es aconsejable hacer esto?
¿Qué versión me recomiendan?
Una vez instalada, ¿qué comando tengo que tipear para actualizar el apt y no volver a tener problemas?

Estoy a la espectativa de cualquier otra seugerencia. 

Muchas gracias!!!!!
Si volves a instalar Flux o cualquier otro sabor "Buntu" que sea de minima 8.10 o superior asi podes actualizar y mantener al dia toda la gestion de paquetes desde los repositorios oficiales, cosa que ahora no podes porque la version 7 (y anteriores) no estan mas soportadas.

---

### Post by Hadso on 2009-05-25
Gracias por el dato, alguna otra sugerencia?
Tengo 256 de RAM me conformo con una version 8 o me tiro a la 9?
Gracias!

---

### Post by guillermolisi on 2009-05-25
> **Hadso said:**
> Gracias por el dato, alguna otra sugerencia?
Tengo 256 de RAM me conformo con una version 8 o me tiro a la 9?
Gracias!
Para poder darte un consejo razonable seria importante conocer las caracteristicas de la maquina: procesador, placa de video, chipset de la maquina, disco.

Por otra parte, con 256 RAM se hara bien dificil instalar desde un LiveCD ya que se requieren por lo menos 128Mb mas para ello.

Mi recomendacion "a priori" es que pruebes con un LiveCD de una y otra version. te fijes que reconoce bien de tu hardware y la que lo haga mejor sea la que termines eligiendo.

Luego, para instalar, usaria un CD Alternate de esa version elegida.
Las versiones de CD alternate te facilitan las cosas al momento de instalar con bajos recursos de maquina.

---

### Post by Hadso on 2009-05-25
> **guillermolisi said:**
> Para poder darte un consejo razonable seria importante conocer las caracteristicas de la maquina: procesador, placa de video, chipset de la maquina, disco.

Por otra parte, con 256 RAM se hara bien dificil instalar desde un LiveCD ya que se requieren por lo menos 128Mb mas para ello.

Mi recomendacion "a priori" es que pruebes con un LiveCD de una y otra version. te fijes que reconoce bien de tu hardware y la que lo haga mejor sea la que termines eligiendo.

Luego, para instalar, usaria un CD Alternate de esa version elegida.
Las versiones de CD alternate te facilitan las cosas al momento de instalar con bajos recursos de maquina.

Tengo un AMD Athlon64, una mother on-board Asus, en cuatno a placa de video no sabría decirte, pero no es nada del otro mundo. Estoy lideando con una PC que tiene mas de 4 años. 
Instalar desde un LiveCD es imposible. Ni siquiera pude instalar el Ubuntu 7.10 y menos aún el Xubuntu, pero este porque me daba problemas para formatear el HD. 
Mi idea es instalar algo de su familia, dado que tengo Xubuntu en la Notebook y me funciona realmente bien. 
No he podido encontrar otras versiones de Fluxbuntu, así que trataré de buscar info sobre el Arternate CD, algo de lo que me acabo de enterar, y trataré de instalar algun SO. 
Muchas gracias por la ayuda. 
Escucho cualquier sugerencia. 
Gracias!

---

### Post by Hei Ku on 2009-05-25
Proba instalando desde el AlternateCD, no desde el Live.
Yo tengo Xubuntu 9.04 en una notebook PIII con 256MB y anda de diez.

---

### Post by Hadso on 2009-05-25
> **Hei Ku said:**
> Proba instalando desde el AlternateCD, no desde el Live.
Yo tengo Xubuntu 9.04 en una notebook PIII con 256MB y anda de diez.

Ya me estuve informando sobre el tema del Alternate. Voy a tratar de meter o bien un Ubuntu o un Xubuntu. 
Gracias!

---

### Post by guillermolisi on 2009-05-25
> **Hadso said:**
> Ya me estuve informando sobre el tema del Alternate. Voy a tratar de meter o bien un Ubuntu o un Xubuntu. 
Gracias!
Mantenete en Xubuntu o, en su defecto, Ubuntu pero solamente con LXDE que me parece algo mas liviano que XFCE.

---

### Post by Hadso on 2009-05-25
Ya tengo el Ubuntu 9 con LXDE y funciona perfecto. Gracias. 
Ahora bien el problema es el siguiente: 
Tengo un disco con dos particiones. Una con XP y otra con el Ubuntu9. 
No me permite abrir ese disco desde el Dolphin ni ningún otro explorador. 
Me dice que hay un error en kdesu o algo así. 
Alguien me puede decir que pasa? Así cerramos este hilo. 
Gracias!

---

### Post by staar on 2009-05-25
primero tenés que montar el disco, y tenés que tener permisos para ello, por eso te tira error dolphin (dolphin con LXDE???)

la forma más fácil sería agregar la partición al fstab, para que el sistema la monte al inicio, para ello necesitarías agregar a tu archivo /etc/fstab una línea similar a la siguiente ```

/dev/sdxX  */punto/de/montaje*   defaults,locale=es_AR.UTF-8              0 0
``` donde sdxX representa la partición de windos (puede ser sda1, sdb2, sda7, etc, depende de tu sistema, averiguala con un sudo fdisk -l), /punto/de/montaje es la carpeta donde se va a montar la partición (tenés que crearla previamente con sudo mkdir /punto/de/montaje) generalmente es una carpeta como /media/winxp o /media/disco o con el nombre que quieras...

OJO esa línea es válida si la partición es NTFS...

saludos

---

### Post by Hadso on 2009-05-26
> **staar said:**
> primero tenés que montar el disco, y tenés que tener permisos para ello, por eso te tira error dolphin (dolphin con LXDE???)

la forma más fácil sería agregar la partición al fstab, para que el sistema la monte al inicio, para ello necesitarías agregar a tu archivo /etc/fstab una línea similar a la siguiente ```

/dev/sdxX  */punto/de/montaje*   defaults,locale=es_AR.UTF-8              0 0
``` donde sdxX representa la partición de windos (puede ser sda1, sdb2, sda7, etc, depende de tu sistema, averiguala con un sudo fdisk -l), /punto/de/montaje es la carpeta donde se va a montar la partición (tenés que crearla previamente con sudo mkdir /punto/de/montaje) generalmente es una carpeta como /media/winxp o /media/disco o con el nombre que quieras...

OJO esa línea es válida si la partición es NTFS...

saludos

Hola. Gracias por la ayuda, pero no me ha servido. :(
Coloqué la siguiente linea en el archivo que me dijiste: 

/dev/sda1  /media/Win   defaults,locale=es_AR.UTF-8              0 0

Creé la carpeta Win, tuve cuidado con la mayúscula, etc. 
Pero en el Dolphin (qué tiene de malo, lo uso porque es el único que conozco :P ) me dice que no tengo permiso para montar esa carpeta en el fichero Win. 
Qué hice mal?
Gracias!

PD: esto es lo que me devuelve el comando fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4d044d03

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5343        9729    35238577+  83  Linux
/dev/sda3            5100        5342     1951897+   5  Extendida
/dev/sda5            5100        5342     1951866   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 2074 MB, 2074345472 bytes
64 cabezas, 62 sectores/pista, 1021 cilindros
Unidades = cilindros de 3968 * 512 = 2031616 bytes
Identificador de disco: 0x20736f63

Esto no parece una tabla de particiones
Probablemente ha seleccionado el dispositivo que no era.

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   ?      483147      620338   272185273   6f  Desconocido
La partición 1 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(361, 101, 36) lógicos=(483146, 62, 10)
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(255, 115, 46) lógicos=(620337, 8, 15)
La partición 1 no termina en un límite de cilindro.
/dev/sdb2   ?      338417      534817   389657273   69  Desconocido
La partición 2 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(100, 101, 32) lógicos=(338416, 24, 48)
La partición 2 tiene distintos finales físicos/lógicos:
     físicos=(367, 115, 35) lógicos=(534816, 14, 13)
La partición 2 no termina en un límite de cilindro.
/dev/sdb3   ?       42503       42503           0   20  Desconocido
La partición 3 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(353, 117, 46) lógicos=(42502, 18, 17)
La partición 3 tiene distintos finales físicos/lógicos:
     físicos=(355, 116, 37) lógicos=(42502, 18, 16)
La partición 3 no termina en un límite de cilindro.
/dev/sdb4          727239      727253       27619    0  Vacía
La partición 4 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(0, 0, 0) lógicos=(727238, 12, 25)
La partición 4 tiene distintos finales físicos/lógicos:
     físicos=(0, 0, 0) lógicos=(727252, 7, 20)
La partición 4 no termina en un límite de cilindro.


GRACIAS!!!!

---

### Post by staar on 2009-05-26
perdón, pero me equivoqué en la linea, al parecer borré sin querer la parte donde se especifica el tipo de sistema de archivos, en realidad la línea sería así ```
/dev/sdxX  /punto/de/montaje  ntfs-g  defaults,locale=es_AR.UTF-8              0 0
``` y si estás usando LXDE, el programa que cumple la misma función que dolphin (que es de KDE) se llama PcManFM, y supongo que ya lo tendrás instalado, de más está decir que es mucho más liviano que Dolphin, así como LXDE es más liviando que KDE...

saludos

---

### Post by Hadso on 2009-05-27
> **staar said:**
> perdón, pero me equivoqué en la linea, al parecer borré sin querer la parte donde se especifica el tipo de sistema de archivos, en realidad la línea sería así ```
/dev/sdxX  /punto/de/montaje  ntfs-g  defaults,locale=es_AR.UTF-8              0 0
``` y si estás usando LXDE, el programa que cumple la misma función que dolphin (que es de KDE) se llama PcManFM, y supongo que ya lo tendrás instalado, de más está decir que es mucho más liviano que Dolphin, así como LXDE es más liviando que KDE...

saludos

Gracias. Pero no me ha funcionado. 
Dice que sólo el usuario root puede montar ese dispositivo. 
Para editar el archivo utilicé "sudo nano /etc/fstab". 
Ayer le puse 1GB mas de RAM a la máquina, con Ubuntu 9 y LXDE quedó como nueva y andando bastante rápido. Así que el Dolphin no es rival... jajajaja
Y con este tema que puedo hacer?
Gracias por tu ayuda!

---

### Post by staar on 2009-05-27
ahora veo que me volví a equivocar en la línea, no doy pie con bola chee...
me faltó un 3, la línea es así: ```
/dev/sdxX  /punto/de/montaje  ntfs-3g  defaults,locale=es_AR.UTF-8              0 0
``` después reiniciá para que se apliquen los cambios...

saludos

---

### Post by WanderingKnight on 2009-05-28
No hace falta reiniciar. Con sudo mount -a el sistema monta todo lo que encuentra en el fstab.

---

### Post by Hadso on 2009-05-29
> **WanderingKnight said:**
> No hace falta reiniciar. Con sudo mount -a el sistema monta todo lo que encuentra en el fstab.

Gracias. Funcionó a la perfección...
GRACIAS!!!!

Este hilo ya se puede cerrar.

---

