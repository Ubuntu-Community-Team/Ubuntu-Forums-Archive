---
title: "no lo puedo creer, no me monta la partición NTFS"
date: 2009-11-17
forum: Software
---

### Post by nahuel_89p on 2009-11-17
no entiendo, siempre me montaba bien la partición NTFS, ahi es donde tengo toda mi musica, peliculas, imagenes, etc, la llego a haber perdido y que hago?? por favor diganme que no es nada grave...

si intento acceder desde el nautilus me dice "Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/disk"

intento con sudo, pero ni siquiera figura.

Lo peor de todo es que el error apareción de la nada! lo ultimo que habia hecho fue instalar el svn, antes de eso poner unos screenlets que "leen" a esa partición (en materia de memoria disponible), y antes de eso habia redimensionado (achicado) una partición ext3, motivo por el cual me quedaron 15 GB sin asignar. De todos modos esto fue hace varios dias, y desde entonces reinicé la computadora incontables veces sin ningun problema. (les digo estos datos por si sirven, pero no creo que tengan mucho que ver)
AYUDA! necesito los datos de esa partición si o si!

P.D: tengo karmic
P.D2: esta es la estructura de particiones:


Tengo 1 disco duro, con las siguientes particiones:

**/dev/sda1/** (esta es la particion mas grande, de 80 gb, de sistema NTFS, donde tengo peliculas y musica)
**/dev/sda2/** (Adentro de esta partición tengo varias particiones: )
**--/dev/sda8/** (mi directorio raíz /... de 15 gb, Ext3)
**--/dev/sda9/** (una swap)
**--/dev/sda5/** (otra swap)
**--/dev/sda6/** (una partición ext3 de 300 mb, la reduje completamente porque no quería borrarla y hacer macana)
**--sin asignar** 15GB libres
**--/dev/sda7/** (otra swap)

---

### Post by jpmorelli on 2009-11-17
Lo primero que tenés que hacer es estar calmado, no te apresures con ninguna decisión. 
Por empezar te recomiendo que no pases ningun tipo de chequeador de particiones etc. ya que si está mal declarada podés hacer un desastre más grande. Googlea por el error exacto y busca más de una solución, para comenzar analizando desde la más simple hasta la más compleja, yo puse el error así nomás en google y saltaron varios que tienen el mismo tema, asi que eso en cierta forma es bueno.
Que ensalada de particiones tenés ! y porque tenés los datos en una NTFS ? Es un windows ? Si es así me imagino que probaste ingresar por ahí no ?
Si una partición windows no esta bien cerrada, estilo se colgó y rearranco el sistema en Ubuntu, el linux generalmente no puede montar el sistema estando "sucio".
Disculpá que no tenga la solución mágica que supongo esperás, pero quería por lo menos prevenirte lo antes posible que no te apures con nada, los datos están, cuanto menos se manoseen mejor. Hay que encontrar la solución correcta, nada más. Y seguramente es más fácil de lo que uno imagina.
Si me entero de algo que tenga buenos fundamentos chiflo.

---

### Post by jpmorelli on 2009-11-17
O sea, para ir aclarando.

Si vos hacés 

sudo mount -t ntfs-3g /dev/sda1 /media/disk/

que error tira ?

---

### Post by nahuel_89p on 2009-11-17
> **jpmorelli said:**
> Lo primero que tenés que hacer es estar calmado, no te apresures con ninguna decisión. 
Por empezar te recomiendo que no pases ningun tipo de chequeador de particiones etc. ya que si está mal declarada podés hacer un desastre más grande. Googlea por el error exacto y busca más de una solución, para comenzar analizando desde la más simple hasta la más compleja, yo puse el error así nomás en google y saltaron varios que tienen el mismo tema, asi que eso en cierta forma es bueno.
Que ensalada de particiones tenés ! y porque tenés los datos en una NTFS ? Es un windows ? Si es así me imagino que probaste ingresar por ahí no ?
Si una partición windows no esta bien cerrada, estilo se colgó y rearranco el sistema en Ubuntu, el linux generalmente no puede montar el sistema estando "sucio".
Disculpá que no tenga la solución mágica que supongo esperás, pero quería por lo menos prevenirte lo antes posible que no te apures con nada, los datos están, cuanto menos se manoseen mejor. Hay que encontrar la solución correcta, nada más. Y seguramente es más fácil de lo que uno imagina.
Si me entero de algo que tenga buenos fundamentos chiflo.

No tengo windows, esa NTFS me quedó de cuando tenía windows... y hay muchas swaps porque reinstalé ubuntu varias veces. Me acuerdo que cuando pasaba esto, bastaba con arrancar con windows y apagar la compu y volver a arrancar ubuntu, y la NTFS se montaba bien, pero hace años que no tengo windows. 
Y con respecto a no probar nada, todavia no traté de hacer nada.

---

### Post by nahuel_89p on 2009-11-17
> **jpmorelli said:**
> O sea, para ir aclarando.

Si vos hacés 

sudo mount -t ntfs-3g /dev/sda1 /media/disk/

que error tira ?

nahuel@nahuel-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk/
[sudo] password for nahuel:
fuse: failed to access mountpoint /media/disk/: No existe el fichero ó directorio
nahuel@nahuel-desktop:~$

---

### Post by jpmorelli on 2009-11-17
Existe el punto de montaje /media/disk    ???

Acabo de correr el comando con mi partición ntfs y lo quise montar sobre un directorio que no tengo y a que no sabés ?
El mismo error que a vos !!! :)

El problema debe estar ahí, seguramente se te borró el directorio donde montabas el disco.

---

### Post by nahuel_89p on 2009-11-17
> **jpmorelli said:**
> Existe el punto de montaje /media/disk    ???

Acabo de correr el comando con mi partición ntfs y lo quise montar sobre un directorio que no tengo y a que no sabés ?
El mismo error que a vos !!! :)

El problema debe estar ahí, seguramente se te borró el directorio donde montabas el disco.

como verifico si existe el punto de montaje /media/disk?

Ahora te pregunto... decís que tenes el mismo error que yo, osea que no podes montar la NTFS??
me quiero matar...


ah, y te comento esto por si te sirve... cuando solía tener windows y ubuntu en la misma computadora, a veces no podía montar la NTFS, y cuando me pasaba eso, creo que bastaba con iniciar windows, apagar, y volver a iniciar ubuntu... despues de ese procedimiento sí se podia montar la ntfs. Aunque tomalo con pinzas porque no se si se trata de exactamente el mismo error

---

### Post by jpmorelli on 2009-11-17
> **nahuel_89p said:**
> como verifico si existe el punto de montaje /media/disk?

Ahora te pregunto... decís que tenes el mismo error que yo, osea que no podes montar la NTFS??
me quiero matar...

No no, yo puedo, pero lo hice mal para ver que error me daba. Te agradezco igualmente por tu preocupación pero quedate tranquilo, lo mio esta todo bien.

Para resumir hace lo siguiente, andá a la terminal y ponés:

cd /media

sudo mkdir disk

sudo mount -t ntfs-3g /dev/sda1 /media/disk/

La primera línea cambia al directorio /media
La segunda crea el directorio disk
La tercera ya sabés :P

Suerte !

---

### Post by nahuel_89p on 2009-11-17
> **jpmorelli said:**
> No no, yo puedo, pero lo hice mal para ver que error me daba. Te agradezco igualmente por tu preocupación pero quedate tranquilo, lo mio esta todo bien.

Para resumir hace lo siguiente, andá a la terminal y ponés:

cd /media

sudo mkdir disk

sudo mount -t ntfs-3g /dev/sda1 /media/disk/

La primera línea cambia al directorio /media
La segunda crea el directorio disk
La tercera ya sabés :P

Suerte !

GROSO! ff anduvo.. mil gracias, copio esto por si me llega a pasar de vuelta... mientras tanto
me interesaría tener una instalación bien en "limpio" del ubuntu... basicamente copiaria todos mis datos a un disco usb... despues instalaria un ubuntu nuevo en el disco duro, porque tengo un lio de particiones que no ayuda... y eso de andar con ntfs ya no me convence.

---

### Post by jpmorelli on 2009-11-17
> **nahuel_89p said:**
> GROSO! ff anduvo.. mil gracias, copio esto por si me llega a pasar de vuelta... mientras tanto
me interesaría tener una instalación bien en "limpio" del ubuntu... basicamente copiaria todos mis datos a un disco usb... despues instalaria un ubuntu nuevo en el disco duro, porque tengo un lio de particiones que no ayuda... y eso de andar con ntfs ya no me convence.

Me alegro que lo hayas solucionado, ponele solved al post.
Cuando tengas el disco listo para formatear todo te recomiendo que le hagas particiones manualmente para que cada vez que quieras actualizar de versión lo puedas si querés hacer con un sistema limpio siempre sin tener que pasar tus datos a otro lado.
Armate:

Una partición de no menos de 8Gb para el Ubuntu raiz ( o sea "/" ), ext4. El sistema en sí utiliza muchísimo menos, pero esto te deja lugar a temporales y pruebas de mas de un gestor de tareas pesados, etc.

Segunda partición con el doble exacto de memo ram que tengas para swap.

Tercera particion con el resto del disco donde ponés tu "/home", ext4

Suerte ! ;)

---

