---
title: "Restringir acceso particion ntfs"
date: 2008-06-06
forum: Software
---

### Post by marcosconio on 2008-06-06
Hola que tal!

Tengo una particion ntfs donde tengo mis documentos personales, una suerte de home pero la uso tambien para acceder a los archivos desde xp cuando lo necesito. 
Lo que necesito hacer es simple, pero no me sale. No quiero que los otros usuarios accedan a esa particion, que solo yo pueda acceder a ella. Se que deberia hacerlo modificando el /etc/fstab, pero por mas que leo no se que opciones ponerle.

Muchas gracias!

Saludos, Marcos

---

### Post by anarko on 2008-06-06
Si la sacas del fstab completamente la particion los solo los "sudoers" ( en ubuntu los usuarios del grupo admin) pueden montarla.Si lo otros usuarios que tenes en la PC no tienen privilegios de sudoers no van a poder ver nada de nada.

---

### Post by marcosconio on 2008-06-07
> **anarko said:**
> Si la sacas del fstab completamente la particion los solo los "sudoers" ( en ubuntu los usuarios del grupo admin) pueden montarla.Si lo otros usuarios que tenes en la PC no tienen privilegios de sudoers no van a poder ver nada de nada.

Eso estaria bien, pero la idea no es tener que montarla explicitamente por mi cada vez que quiero usarla, sino que el "dueño" de la particion sea el usuario "marcos", para usarla apenas me logueo, y que los otros usuarios aunque puedan verla no puedan acceder a ella.
Tal vez podria hacer lo que decis, y poner la sentencia del mount en mi .bashrc? O en algun otro archivo que se ejecute solo para mi?

Gracias, Marcos

---

### Post by anarko on 2008-06-07
Eso seria una solucion.

---

### Post by marcosconio on 2008-06-11
> **anarko said:**
> Si la sacas del fstab completamente la particion los solo los "sudoers" ( en ubuntu los usuarios del grupo admin) pueden montarla.Si lo otros usuarios que tenes en la PC no tienen privilegios de sudoers no van a poder ver nada de nada.

Lo saco completamente del fstab, y nos deja a todos los usuarios montarlo automaticamente. Si voy en el menu a "Lugares-Docs", donde "docs" es el nombre de la particion, me lo monta solo, y deja visible la particion y todos los archivos para cualquier usuario. 
Como podria hacer para cambiar eso?

Gracias, Marcos

---

### Post by Mister X on 2008-06-11
Podes hacerlo editando el fstab, fijate que en las opciones te debe apareces gid=xxx (un numero)  esto significa que va a montarlo con permisos para el grupo xxx, lo quetenes que hacer es sacar la opcion gid y en su lugar poner uid=xxx (tu user ID), en mi caso quedaria asi:

```
UUID=74D4CA87D4CA4AD6 /media/sda1     ntfs    defaults,rw,nls=utf8,umask=007,uid=1000 0       1

```

---

### Post by marcosconio on 2008-06-12
> **Mister X said:**
> Podes hacerlo editando el fstab, fijate que en las opciones te debe apareces gid=xxx (un numero)  esto significa que va a montarlo con permisos para el grupo xxx, lo quetenes que hacer es sacar la opcion gid y en su lugar poner uid=xxx (tu user ID), en mi caso quedaria asi:

```
UUID=74D4CA87D4CA4AD6 /media/sda1     ntfs    defaults,rw,nls=utf8,umask=007,uid=1000 0       1

```

Paso a mostrarte:
La linea correspondiente del fstab es:
```
UUID=E460F46B60F44638 /media/docs     ntfs    defaults,rw,umask=007,uid=1000 0       1
```
Y el ls sobre /media me da:
```
marcos@marcos-laptop:~$ ls -l /media/
total 20
lrwxrwxrwx 1 root       999    6 2008-05-02 11:27 cdrom -> cdrom0
drwxr-xr-x 2 root       999 4096 2008-05-02 11:27 cdrom0
drwxrwx--- 1 root   plugdev 4096 2008-06-12 09:37 datos
drwxrwx--- 1 marcos root    8192 2008-06-12 09:37 docs
drwxr-xr-x 2 root       999 4096 2008-05-02 11:27 windows

```
O sea que los permisos estan bien seteados. Lo que me extraña es que si me logueo como otro usuario que no sea marcos, puedo hacer lo que sea sobre esa particion. Y si verifico los grupos a los que pertenece el otro usuario, no veo que pertenezca al grupo "root".

Marcos

---

### Post by Mister X on 2008-06-12
> **marcosconio said:**
> 
O sea que los permisos estan bien seteados. Lo que me extraña es que si me logueo como otro usuario que no sea marcos, puedo hacer lo que sea sobre esa particion. Y si verifico los grupos a los que pertenece el otro usuario, no veo que pertenezca al grupo "root".

Marcos

Es raro, recien estube probando, con el ls obtengo la misma informacion que vos. Si intento acceder desde la consola con otro usuario, me dice permiso denegado y con el nautilus directamente ni veo la particion, o sea que me funciona bien.
Probá de modificar la opcion umask para que quede: umask=077 , de esta manera lo va a montar con permisos solo para el propietario.

---

### Post by marcosconio on 2008-06-13
> **Mister X said:**
> Es raro, recien estube probando, con el ls obtengo la misma informacion que vos. Si intento acceder desde la consola con otro usuario, me dice permiso denegado y con el nautilus directamente ni veo la particion, o sea que me funciona bien.
Probá de modificar la opcion umask para que quede: umask=077 , de esta manera lo va a montar con permisos solo para el propietario.

Ok, estoy en la sesion de mi hermano, mira esto, no es raro? Hay algo que me enseñaron en sistemas operativos que no me cuadra:

```
emi@marcos-laptop:~$ ls -l /media/
total 20
lrwxrwxrwx 1 root       999    6 2008-05-02 11:27 cdrom -> cdrom0
drwxr-xr-x 2 root       999 4096 2008-05-02 11:27 cdrom0
drwxrwx--- 1 root   plugdev 4096 2008-06-12 09:37 datos
drwx------ 1 marcos root    8192 2008-06-12 09:37 docs
drwxr-xr-x 2 root       999 4096 2008-05-02 11:27 windows
emi@marcos-laptop:~$ ls -l /media/docs/
total 20752
drwx------ 1 marcos root     4096 2008-06-11 23:24 archivosPersonales
-rwx------ 1 marcos root    29623 2008-06-01 12:32 compizConfiguraciones.profile
drwx------ 1 marcos root     4096 2008-06-10 22:21 desarrollos
drwx------ 1 marcos root        0 2008-04-24 21:13 empresas
-rwx------ 2 marcos root 21168647 2008-03-09 14:26 iconos-netByteDesignStudio.tar.gz
drwx------ 1 marcos root    16384 2008-06-08 23:25 imagenes
drwx------ 1 marcos root     4096 2008-06-11 08:54 info cds
drwx------ 1 marcos root        0 2008-03-09 14:26 lost+found
drwx------ 1 marcos root     4096 2008-03-26 22:47 motorola L7 Marcos
drwx------ 1 marcos root     4096 2008-04-13 21:42 $RECYCLE.BIN
drwx------ 1 marcos root     4096 2008-05-11 15:38 RECYCLER
drwx------ 1 marcos root     4096 2008-05-11 13:26 System Volume Information
emi@marcos-laptop:~$
```

Porque el usuario emi puede leer el directorio, si le pertenece a marcos? Es raro...
Sabes que cuando le doy al icono de la particion que tengo en el escritorio con el boton derecho del mouse, le doy a propiedades, la última pestaña es una que dice "Volume". Lo que me muestra esta pestaña es: 
```
Punto de montaje:   /media/docs
Sistema de archivos: fuseblk
Opciones de montaje: rw nosuid nodev noatime relatime user_id=0 group_id=0 default_permissions allow_other
```
Esto me llamó mucho la atención, por las opciones mas que nada...
Tendre que cambiar algo por aca?

Gracias, Marcos

---

### Post by faktorqm on 2008-06-13
El problema ahi, es que ubuntu no te toma los permisos por que la particion es ntfs. Probá de comentar la linea en el fstab. Creo que haciendo eso, al no estar la particion definida en el fstab, si o si necesitas ser root para montarla. Conta como te fue. Salu2!!

---

### Post by marcosconio on 2008-06-13
> **faktorqm said:**
> El problema ahi, es que ubuntu no te toma los permisos por que la particion es ntfs. Probá de comentar la linea en el fstab. Creo que haciendo eso, al no estar la particion definida en el fstab, si o si necesitas ser root para montarla. Conta como te fue. Salu2!!

Aunque la borre o la comente, igual pueden montarla los otros usuarios. Simplemente se van a "Lugares-Docs". Hacen click ahi, y eso les monta automaticamente la particion en /media/docs. Eso ya lo probe antes, asique por ahi tampoco va la solucion.

Saludos, Marcos

---

### Post by faktorqm on 2008-06-13
Entonces ponele nouser a la linea, a ver que pasa. Salu2!

---

### Post by Mister X on 2008-06-13
Yo todavia estoy en Gusty, vos estas en Hardy Marcos?
No cambió algo con el manejo de la seguridad? Leí algo por ahi, pero la verdad que no tengo idea, tal vez tenga algo que ver con esto ya que de otra manera no me explico...

---

### Post by marcosconio on 2008-06-13
> Entonces ponele nouser a la linea, a ver que pasa. Salu2!


```
UUID=E460F46B60F44638 /media/docs     ntfs    defaults,nouser,rw,umask=077,uid=1000 0       1
```
Exactamente el mismo resultado

> **Mister X said:**
> Yo todavia estoy en Gusty, vos estas en Hardy Marcos?
No cambió algo con el manejo de la seguridad? Leí algo por ahi, pero la verdad que no tengo idea, tal vez tenga algo que ver con esto ya que de otra manera no me explico...
Si estoy en Hardy, y es probable que haya cambiado algo. Antes tenia Gutsy, y tenia ese problema solucionado, pero me parece que la particion estaba en fat32, no recuerdo bien

EDIT: Mil disculpas, me mareé con las versiones... Tengo Hardy, antes tenía Gutsy.


Gracias por las respuestas, Marcos

---

