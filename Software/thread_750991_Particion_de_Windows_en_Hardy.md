---
title: "Particion de Windows en Hardy"
date: 2008-04-10
forum: Software
---

### Post by santiagoward2000 on 2008-04-10
Hola gente!
Hoy decidí probar Hardy. Todavía no probé todo, todavía estoy instalando cosas (hice un clean install). Pero hay una cosita que noté apenas entré que me molesta: no puedo ver la partición de Windows. ¿Hay algún paquete que tenga que instalar? ¿A alguien más le pasó?
Saludos!

---

### Post by Hei Ku on 2008-04-10
tenes instalado el ntfs-3g?
quizas lo tengas instalado, pero no montada la particion

---

### Post by erginemr on 2008-04-10
Cuales son los resultados de los comandos siguientes:
```
sudo fdisk -l
```
```
blkid
```
```
cat /etc/fstab
```
en la terminal?

---

### Post by santiagoward2000 on 2008-04-10
> **Hei Ku said:**
> tenes instalado el ntfs-3g?
quizas lo tengas instalado, pero no montada la particion

Si, está instalado, pero la partición no aparece en /media, asíque no sé cómo montarla.

> **erginemr said:**
> Cuales son los resultados de los comandos siguientes:
```
sudo fdisk -l
```
```
blkid
```
```
cat /etc/fstab
```
en la terminal?

Acá está:

```
santi@santi-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef30ef30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1963    15767766    7  HPFS/NTFS
/dev/sda2            1964        7296    42837322+   5  Extended
/dev/sda5            1964        7227    42283048+  83  Linux
/dev/sda6            7228        7296      554211   82  Linux swap / Solaris
santi@santi-laptop:~$ blkid
santi@santi-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=d8e1bbf7-57ec-4572-981e-f08f516cf03d /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=ae3bd23c-899d-4917-b1f9-356e6db05390 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Según parece la partición está...
GRACIAS! :)

---

### Post by erginemr on 2008-04-10
No hay problema! Primero, asegúrese de que hay un directorio para su partición de Windows en** /media**:
```
sudo mkdir /media/hda1
```

Entonces, por favor, modifique el archivo **/etc/fstab** con:
```
gksudo gedit /etc/fstab
```
y añada la siguiente línea al final del archivo:
```
/dev/hda1 /media/hda1    ntfs-3g     defaults    0 1
```
Escribe el archivo y reinicie su computadora. Ahora, Ubuntu debería ver su partición de Windows.

---

### Post by erginemr on 2008-04-10
Si la línea arriba no funciona, pruebe este en lugar de esta:
```
sudo mkdir /media/sda1
```
```
/dev/sda1 /media/sda1    ntfs-3g     defaults    0 1
```

Buena suerte!..

---

### Post by santiagoward2000 on 2008-04-10
> **erginemr said:**
> Si la línea arriba no funciona, pruebe este en lugar de esta:
```
sudo mkdir /media/sda1
```
```
/dev/sda1 /media/sda1    ntfs-3g     defaults    0 1
```

Buena suerte!..

Muchísimas gracias!
Lo del primer post no anduvo, pero esto sí! :KS
Una pregunta más: Cuando estaba en Gutsy, la partición aparecía como un disco extraíble y yo tenía que montarlo. Ahora, no puedo montar y desmontarlo, viene ya montado, y Hardy no lo detecta como un disco extraíble. ¿Hay alguna forma de hacer esto?
Gracias de nuevo!

---

### Post by sajnox on 2008-04-10
Si queres desmontar el disco lo podes hacer con un click derecho en el disco y elegir desmontar

Tambien lo podes hacer desde una consola con el comando

```
sudo umount /dev/sda1
```

Si queres montarlo nuevamente podes entrar por Lugares\Equipo\ y haces doble click en disco que queres montar y obviamente por consola

```
sudo mount /dev/sda1 /media/sda1
```

---

### Post by santiagoward2000 on 2008-04-10
> **sajnox said:**
> Si queres desmontar el disco lo podes hacer con un click derecho en el disco y elegir desmontar

Si, eso hacía en Gutsy, pero ahora en Hardy la partición no aparece en ningún lado como para hacer click derecho. En Gutsy tenía uno en el escritorio y también en la sidebar de Thunar, pero ahora en Hardy no. :confused:

> **sajnox said:**
> Tambien lo podes hacer desde una consola con el comando

```
sudo umount /dev/sda1
```

Si queres montarlo nuevamente podes entrar por Lugares\Equipo\ y haces doble click en disco que queres montar y obviamente por consola

```
sudo mount /dev/sda1 /media/sda1
```

Gracias por el comando, eso anduvo. Aunque ahora me gustaría poder hacerlo con clicks (si... no me puedo sacar esa costumbre de Windows... :lol:)

_EDIT:_
Recién estuve probando con el LiveCD en mi PC (hasta ahora estaba usando Hardy en mi laptop) y tengo el mismo problema. Tampoco me aparece la partición de Windows. ¿Será un bug en Xubuntu?

---

### Post by erginemr on 2008-04-11
Usted puede tambien añadir un elemento nuevo al panel de xfce para mantener las particiones por el momento. Ver las capturas de pantalla debajo.

---

### Post by santiagoward2000 on 2008-04-11
> **erginemr said:**
> Usted puede tambien añadir un elemento nuevo al panel de xfce para mantener las particiones por el momento. Ver las capturas de pantalla debajo.

Gracias por la sugerencia! :)
Ahora me queda una duda, ¿será un bug que no aparece la partición? ¿Tengo que reportarlo?

---

### Post by erginemr on 2008-04-12
> **santiagoward2000 said:**
> Gracias por la sugerencia! :)
Ahora me queda una duda, ¿será un bug que no aparece la partición? ¿Tengo que reportarlo?

De nada mi amigo. :popcorn:

Creo que sí. Me aparece que hay un bug a Thunar, así puede usted reportarlo.

---

### Post by santiagoward2000 on 2008-04-12
> **erginemr said:**
> De nada mi amigo. :popcorn:

Creo que sí. Me aparece que hay un bug a Thunar, así puede usted reportarlo.

¿Un bug a Thunar? ¿Entonces lo tendría que reportar al equipo de Xubuntu o de Xfce?

---

### Post by Hei Ku on 2008-04-12
cargalo en launchpad, y ellos lo van a derivar a xfce si es necesario

---

### Post by santiagoward2000 on 2008-04-13
> **Hei Ku said:**
> cargalo en launchpad, y ellos lo van a derivar a xfce si es necesario

Listo. Les aviso cuando tenga alguna noticia.
Gracias por la paciencia! :)

---

### Post by tekenika on 2008-09-15
Hola a todos
Acabo de instalar Hardy.(Xubuntu)
Y en relación al asunto tengo algunas dudas.
Antes que nada aqui está mi fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cf1c0a0f-48c5-4c31-9949-294878471f28 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=376b7bb9-cce3-43fa-b970-844844755e8d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=es_AR.UTF-8 0 0
/dev/sdb6 /media/datos ext3  relatime,errors=remount-ro 0
/dev/sdb5 /media/bu vfat   defaults,utf8,umask=007,gid=46   0 0
-------------------
Las dos últimas líneas las agregué yo pues el sistema no lo hizo.
Las dudas:
No monta la lecto-grabadora
Thunar no ofrece con boton derecho la opción de montar
Agregué a la barra de tareas el mount-devices, no sé cual es el comando que debe ponerse, Me muestra las particiones y el cdrom (informa que no está montado) pero no puedo hacer nada.
Yo tengo colgado siempre un disco externo (via USB) que con el sistema recien instalado aparecía siempre montado, no se porque ahora debo montarlo yo.(aparece en lugares)
Alguna vez, en mi Xubuntu anterior, las particiones aparecían en la columna izquierda de Thunar ahora solo aparece el disco externo. Esto puede solucionarse?
Planteo todas las dudas de una vez, porque seguramente están relacionadas
desde ya gracias y saludos

---

