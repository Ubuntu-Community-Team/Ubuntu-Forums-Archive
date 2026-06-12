---
title: "HOW-TO: Montar disco de VirtualBox como una unidad"
date: 2009-08-30
forum: Software
---

### Post by Mauro22 on 2009-08-30
[B][COLOR="Blue"]#!/bin/Mauro22
[/COLOR][/B]
Gente, hoy mi meta fue montar y explorar el disco virtual de VirtualBox (el .vdi) para poder usarlo como cualquier otra unidad...

Vamos con los pasos que no son muchos, pero presten atencion.


****Estos pasos sirven para discos virtuales VDI, VMDK o VHD.**

[guia]

Empecemos a cocinar:

Ingredientes:

1. Gcc 4 o superior
2. VirtualBox 2 o superior
3. Encabezados --> [COLOR="Blue"]sudo apt-get install build-essential[/COLOR]
4. Fuse y sus encabezados --> [COLOR="blue"]sudo apt-get install libfuse-dev[/COLOR]
5. El código de VirtualBox **-o-** subversion --> [COLOR="blue"]sudo apt-get install subversion[/COLOR]



Ready?

1. Bajar "vdfuse-v50.c" y "vdbuild" (Adjuntos más abajo en .tar.gz)

2. Si tenes el codigo de virtualbox --> Paso 4. Si no lo tenes o no sabes de que se trata --> Paso 3.

3. Aplicaciones -> Accesorios -> Terminal

```
svn co http://www.virtualbox.org/svn/vbox/trunk/include/
```

Les generará una carpeta include 

4. Van a la carpeta donde descargaron "vdbuild"

```
nano vdbuild
```
O su editor preferido

En la parte superior encontraran:

```
# INSTALL_DIR - vbox install directory
```
Abajo de eso, ponen el directorio de donde estan las librerias de VirtualBox

****En mi caso fue es '/usr/lib/virtualbox' asi que quedaria algo asi:**

```
INSTALL_DIR=/usr/lib/virtualbox
```

5. Guardan el archivo modificado y le dan permisos de ejecucion

```
chmod +x vdbuild
```

6. Compilamos:

```
sh vdbuild XX vdfuse-v50.c
```

[B]**Donde XX es donde tienen los encabezados de VB. Por ejemplo, yo lo baje por svn asi que me quedo de esta forma. 
Si tienen el codigo de VB apunten a la carpeta que corresponde (include):
[/B]
```
sh vdbuild /home/mauro22/include vdfuse-v50.c
```

7. Les devuelve 'Sucess' y les genera un archivo "vdfuse-v50"

8. Creamos el punto de montaje y montamos el disco virtual. 

```
mkdir /puntodemontaje
```
```
./vdfuse-v50 -f disco.vdi /puntodemontaje
```

La -f indica el archivo. Con -h tienen todos los comandos.

9. Dentro de 'puntodemontaje' tendria que estar:

EntireDisk0 Partition1 Partition2 etc etc

10. Montamos la particion que necesitamos.

```
mkdir /home/mauro22/MI_DISCO_VIRTUAL
```
```
mount -o loop /puntodemontaje/Partition1 /home/mauro22/MI_DISCO_VIRTUAL
```

**** Si lo hacen con sudo y en otros casos le puede dar error y les dice que hagan lo siguiente:**

```
sudo nano /etc/fuse.conf
```

y decomentan: (Sacarle el #)

De esto:
```
#user_allow_other

```A esto:
```
user_allow_other

```

[/guia]



[COLOR="Red"][B]Aclaracion: Como toda letra en rojo... Ejecutese bajo su propio riesgo. Hagase amigo del Backup. Use la opcion -r para que sea de 'solo lectura'.

No lo probé usando usando la maquina virtual, no sé que pasará si se intenta montar o arrancar la MV con el disco montado...[/B][/COLOR]


Fuente: 
- [http://forums.virtualbox.org/viewtopic.php?f=7&t=17574](http://forums.virtualbox.org/viewtopic.php?f=7&t=17574)
- Yo

---

### Post by yojuako on 2010-01-05
buenas,

muy bueno el post, pero me trabe en una parte y me gustaria saber que puede estar andando mal.
llego hasta esta parte bien. 

> 
./vdfuse-v50 -f disco.vdi /puntodemontaje

despues me tira el error de abajo.

```
root@juakoyyo:/home/juako/Escritorio/DESCARGA/montar_dv# ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NO\TOCAR/JUAKO2.vdi /puntodemontaje

ERROR: cannot access imagefile

DESCRIPTION: This Fuse module uses the VirtualBox access library to open a 
VirtualBox supported VD image file and mount it as a Fuse file system.  The
mount point contains a flat directory containing the files EntireDisk,
Partition1 .. PartitionN.  These can then be loop mounted to access the
underlying file systems

USAGE: ./vdfuse-v50 [options] -f image-file mountpoint
	-h	help
	-r	readonly
	-t	specify type (VDI, VMDK, VHD, or raw; default: auto)
	-f	VDimage file
	-a	allow all users to read disk
	-w	allow all users to read and write to disk
	-g	run in foreground
	-v	verbose
	-d	debug

```

bueno, espero me puedan dar una solucion.

desde ya muy agradecido.

gracias

juako

---

### Post by guillermolisi on 2010-01-05
El mensaje de error esta indicando que no encuentra una imagen de disco vdi adecuada.

Revisa el path que te lleva hasta la imagen de disco de VBox. Me da la impresion de que algunos caracteres no estan haciendo buena magia en ese path:

> root@juakoyyo:/home/juako/Escritorio/DESCARGA/montar_dv# ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NO[COLOR=Red]\[/COLOR]TOCAR/JUAKO2.vdi /puntodemontaje
Si despues del directorio TODO sigue otro con nombre VIRTUALBOX-NO(espacio)TOCAR, te prepongo cambiar el espacio por un "_" (sin las comillas) asi te evitas caracteres de filtrado para el parsing y la interpretacion de todo el path.

Por las dudas, considera que en Linux los nombres de directorios/archivos son "case sensitive", es decir, se distingue "VIRTUALBOX" como diferente de "virtualbox".

"puntodemontaje" debe ser un directorio, preferentemente vacio, que se utiliza para "conectar" la estructura interpretada por el utilitario. En tu caso ese directorio estaria creado directamente dependiendo del root directory y con el nombre "puntodemontaje".

---

### Post by yojuako on 2010-01-07
bien, me salio otra cosa cuando saque el espacio del medio en NO TOCAR y puse NOTOCAR todo junto.

me sale lo siguiente:

```
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vmdk /puntodemontaje

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp:2465 (int vmdkValidateHeader(VMDKIMAGE*, VMDKEXTENT*, const SparseExtentHeader*)): VMDK: incorrect version in sparse extent header in '/home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vmdk', not a VMDK 1.0/1.1 conforming file

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VBoxHDD.cpp:1284 (int VDOpen(VBOXHDD*, const char*, const char*, unsigned int, VDINTERFACE*)): Fallo de segmentación
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ 
```


muchas gracias desde ya,

juako

---

### Post by guillermolisi on 2010-01-07
> **yojuako said:**
> bien, me salio otra cosa cuando saque el espacio del medio en NO TOCAR y puse NOTOCAR todo junto.

me sale lo siguiente:

```
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2[COLOR=Red].vmdk[/COLOR] /puntodemontaje

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp:2465 (int vmdkValidateHeader(VMDKIMAGE*, VMDKEXTENT*, const SparseExtentHeader*)): VMDK: incorrect version in sparse extent header in '/home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2[COLOR=Red].vmdk[/COLOR]', not a VMDK 1.0/1.1 conforming file

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VBoxHDD.cpp:1284 (int VDOpen(VBOXHDD*, const char*, const char*, unsigned int, VDINTERFACE*)): Fallo de segmentación
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ 
```muchas gracias desde ya,

juako
El disco de una VM de VBox tiene .vdi como sufijo de su nombre.
Si usas vmdk, por el mensaje de error que te dio, aparenta haber algun problema de compatibilidad, posiblemente generado por la version de VBox con la cual se creo el disco y la actual version de los utilitarios que usas.

---

### Post by yojuako on 2010-01-12
resulta que el archivo original era un VDI
pero en un error lo borre y cuando lo recupere con el PHOTOREC me lo tiro como VMDK

lo mas probable es que este DAÑADO

Habra alguna forma de recuperar los archivos dentro del disco?

hay forma de arreglarlo?

por favor, aunque sea orientame para donde buscar una solucion

muchas gracias

juako

---

### Post by guillermolisi on 2010-01-12
> **yojuako said:**
> resulta que el archivo original era un VDI
pero en un error lo borre y cuando lo recupere con el PHOTOREC me lo tiro como VMDK

lo mas probable es que este DAÑADO

Habra alguna forma de recuperar los archivos dentro del disco?

hay forma de arreglarlo?

por favor, aunque sea orientame para donde buscar una solucion

muchas gracias

juako
Que pasa si renombras para que tenga sufijo .vdi ? Da los mismos errores ?

Los archivos que queres recuperar son los que estan en el disco virtual o en el fisico ?

---

### Post by yojuako on 2010-01-13
me sale este error

```
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vdi /puntodemontaje

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp:2465 (int vmdkValidateHeader(VMDKIMAGE*, VMDKEXTENT*, const SparseExtentHeader*)): VMDK: incorrect version in sparse extent header in '/home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vdi', not a VMDK 1.0/1.1 conforming file

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VBoxHDD.cpp:1284 (int VDOpen(VBOXHDD*, const char*, const char*, unsigned int, VDINTERFACE*)): Fallo de segmentación
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ 

```

creo que es el mismo que me hacia cuando era un VMDK.

los archivos que quiero recuperar estan dentro del disco virtual que cree en virtualBox en su momento y que ahora estoy tratando de hacer correr para sacar lo que necesito.

muchas gracias por la ayuda.

juako

---

### Post by guillermolisi on 2010-01-13
> **yojuako said:**
> me sale este error

```
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ ./vdfuse-v50 -f /home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vdi /puntodemontaje

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp:2465 (int vmdkValidateHeader(VMDKIMAGE*, VMDKEXTENT*, const SparseExtentHeader*)): VMDK: incorrect version in sparse extent header in '/home/juako/Escritorio/TODO/VIRTUALBOX-NOTOCAR/JUAKO2.vdi', not a VMDK 1.0/1.1 conforming file

VD CallbackError rc -3241 at /home/vbox/vbox-3.1.2/src/VBox/Devices/Storage/VBoxHDD.cpp:1284 (int VDOpen(VBOXHDD*, const char*, const char*, unsigned int, VDINTERFACE*)): Fallo de segmentación
juako@juakoyyo:~/Escritorio/DESCARGA/montar_dv$ 

```creo que es el mismo que me hacia cuando era un VMDK.

los archivos que quiero recuperar estan dentro del disco virtual que cree en virtualBox en su momento y que ahora estoy tratando de hacer correr para sacar lo que necesito.

muchas gracias por la ayuda.

juako
Si, es el mismo error que antes porque en realidad VBox revisa el encabezado del archivo y detecta que es VMDK por mas que le pongas lo que pongas al nombre:> 
(int vmdkValidateHeader(VMDKIMAGE*, VMDKEXTENT*, const SparseExtentHeader*)

Si el archivo esta corrupto tal vez en el sitio de Sun/Vbox den alguna idea de como repararlo, de ser esto posible.

---

### Post by Mauro22 on 2010-01-16
Perdon... ya volví de mis vacaciones :P


Trata de montar ese disco primero en un maquina virtual como esclavo (o no booteable, en su defecto) y ver como esta la integridad del FileSystem. 

Una vez montado, podes correr herramientas de diagnostico para repararlo si hace falta.


Luego, volver a intentar la guia.

---

### Post by grtouron on 2012-03-11
Hola:

No puedo compilar. Pongo:

sh vdbuild /home/grtouron/include vdfuse-v50.c

y me responde:

Invalid include directory. Make sure that it has the VBox directory inside.

Ciertamente, el directorio "/home/grtouron/include" tiene una carpeta VBox adentro. ¿Qué puede estar pasando?

Gracias y saludos,

Gastón

---

