---
title: "Problemas con el grub al clonar  hd"
date: 2009-09-10
forum: Software
---

### Post by edudelsur on 2009-09-10
que tal soy nuevo en ubuntu por lo que mucho no entiendo, siempre trabajé con Windows,
el tema es que tengo una sala de informática a cargo y quiero instalarle los dos SO, de hecho lo hise con una máquina con buenos resultados, ahora tengo 15 máquinas más!! por lo que desidí usar gosth para clonar los HD y ahorrarme el trabajo de reinstalar todo en las demas máquinas, Pero tengo problemas con el GRUB no arranca el multibooteo la máquina con el HD clonado queda repitiendo GRUB por toda la pantalla, ¿PUEDO SOLUCIONARLO? ¿ALGUIEN SABE COMO HACERLO?

---

### Post by pablo.s on 2009-09-10
> **edudelsur said:**
>  por lo que desidí usar gosth para clonar los HD y ahorrarme el trabajo de reinstalar todo en las demas máquinas, Pero tengo problemas con el GRUB no arranca el multibooteo la máquina con el HD clonado queda repitiendo GRUB por toda la pantalla,

GRUB consta de dos partes:
la parte de configuración, que
se instala en / y la parte del
cargador de arranque, que por
lo general se instala en la MBR.
Estoy casi seguro que Norton Ghost
no toca la MBR, asi que...
Respirá hondo, fijate de hacer cinco
o seis copias para instalar al mismo
tiempo, asi se te hace más leve.

---

### Post by staar on 2009-09-10
o podés usar [supergrubdisk]("http://www.supergrubdisk.org") para escribir GRUB en la MBR de todas las máquinas, así te ahorras mucho tiempo...

saludos

---

### Post by gmunioz on 2009-09-10
Hola edu....:

Te falto clonar el mbr.

Esto se hace con el comando dd

En el primer ordenador, de donde

se ha de clonar el sistema con

la orden:

sudo dd if=/dev/sda of=mbr.backup bs=512 count=1


Creas en el directorio (carpeta) donde te encuentras

seguramente /home/tuusuario/ el archivo mbr.backup

que corresponde a la clonación/copia del mbr

Luego en cada uno de los ordenadores, desde una

sesión live, teniendo copiado dicho archivo mbr.backup

en el directorio /home/usuario de la sesión live

con la orden 

sudo dd if=mbr.backup of=/dev/sda bs=512 count=1

completas la clonación de la instalación

Partimage, es el equivalente al Norton Ghost en

GnuLinux.

Si en el sistema esta instalado tambien MS Windows puede

que este utilizando GUID, el cual utiliza más sectores para 

guardar la información sobre las particiones del disco duro. 

Las instrucciones serian entonces las siguientes:

Para crear el archivo

sudo dd if=/dev/sda of=mbr_63.backup bs=512 count=63

Para clonar el mbr 

sudo dd if=mbr_63.backup of=/dev/sda bs=512 count=63 

Para el caso que sea necesario borrar el mbr, no la información

del disco, aunque quedaría inaccesible la misma, la orden es:

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

-----edito------------

Ahora si aun no has clonado los discos un sistema practico

sin necesidad de aplicaciones es colocar en el ordenador

con el sistema instalado, el disco clon y clonar el original

con la orden:

sudo dd if=/dev/sda of=/dev/sdb bs=1M

donde /dev/sda es el disco con el sistema y /dev/sdb 

es el disco sin sistema

------nueva edicion---------------

Existe una aplicación  con licenciamiento GNU/GPL Clonezilla.

Muy utilizada para clonar múltiples ordenadores con similar configuración.

Permite crear una imagen del disco, de un sistema completamente instalado 

y funcionando perfectamente, para guardarla en un dispositivo tal como

otra unidad de disco, partición, dispositivo USB o servidor, etc. 

Viene en dos versiones disponibles:

Clonezilla Server Edition (SE)

Clonezilla Live. 

La versión SE usa multidifusión para clonar múltiples ordenadores en red

en forma simultanea, incluso en forma remota si existe soporte para 

Wake-on-LAN y PXE.

Como Clonezilla guarda la información  en un formato propio y con compresión

la imagen resultante siempre es mucho menor que la del disco clonado.

----------fin edicion-------

---

### Post by adrian15 on 2009-09-24
> **edudelsur said:**
> Pero tengo problemas con el GRUB no arranca el multibooteo la máquina con el HD clonado queda repitiendo GRUB por toda la pantalla, ¿PUEDO SOLUCIONARLO? ¿ALGUIEN SABE COMO HACERLO?

Haz el favor de clonar el disco duro y no únicamente la partición de Linux, si es que Ghost es capaz de hacerlo, claro está.

adrian15

---

### Post by edudelsur on 2009-10-01
Gracias a todos por la mano!! lo solucione perfectamente con el Clonezilla

---

### Post by andres2420 on 2009-10-16
Me cuelgo de este tema para consultarles algo que capas es simple pero me causa duda.

Estoy por clonar mi disco completo (2 particiones y un espacio de intercambio) a otro. Con clonezilla o el ghost se compia tal cual todo? la division de las particiones y todo? Y otra cosa que me intriga es que que pasa con el UUID de las particiones? se tiene que modificar esto en el archivo fstab? porque me parece que daria error al arrancar.

---

