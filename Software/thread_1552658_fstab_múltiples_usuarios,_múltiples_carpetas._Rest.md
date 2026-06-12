---
title: "fstab múltiples usuarios, múltiples carpetas. Restringir acceso."
date: 2010-08-13
forum: Software
---

### Post by granjero on 2010-08-13
hola, tengo una duda:

tengo una pc con ubuntu 10.04 donde hay varios usuarios.

Cada uno necesita acceso a distintos directorios de un servidor win2003.

El problema me surge cuando armo el fstab.

Al iniciar sesión todos los usuarios tienen montados todos los directorios que pongo en el fstab. 

Lo que necesito es que monte para cada usuario una carpeta distinta y no todas.

eso es posible?

salud!

---

### Post by guillermolisi on 2010-08-14
Una posibilidad seria con un script que se ejecute con el login de cada uno, montando la particion/disco que corresponda en cada caso.

Manejarlo via permisos a nivel fstab no evitaria que se monte y se vea (caso read only) y creo que seria mas elegante y menos "problematico" (elimina la pregunta "Por que no puedo escribir sobre tal disco si lo estoy viendo en mi escritorio ?") hacerlo via script.

---

### Post by zeroadrenaline on 2010-08-17
> **granjero said:**
> hola, tengo una duda:

tengo una pc con ubuntu 10.04 donde hay varios usuarios.

Cada uno necesita acceso a distintos directorios de un servidor win2003.

El problema me surge cuando armo el fstab.

Al iniciar sesión todos los usuarios tienen montados todos los directorios que pongo en el fstab. 

Lo que necesito es que monte para cada usuario una carpeta distinta y no todas.

eso es posible?

salud!

Fstab tiene parametros como es umask,gmask,uid y gid que te permiten manejar el nivel de permisos por usuario, grupo y demas.
Algunos ejemplos:

```

\\share\win2003\shareA /media/shareA smbfs rw,uid=1001,gid=1001,umask=077,gmask=077

```

Esa linea monta en /media/shareA la unidad de red shareA del win2003 con smbfs como filesystem, el dueño de la unidad es el usuario 1001 y el grupo del mismo id que generalmente pertenece al mismo usuario. Por ultimo umask es l amascara de usuario, que funciona excatamente a la inversa que los permisos de ficheros en sistemas unix like, es decir:
000 = dxrwxrwxrw
777 = ----------

g mask aplica de l amisma forma pero para el grupo 1001.
Jugando con estos parametros podes obtener las opciones que necesitas.
Esta solucion no evita el problema que menciona gillermo, el famoso "Y por que no puedo entrar al disco Yo? UFAAAAAAAAAAAAAA yo quiero entrar al disco!!!!!!!"

---

### Post by granjero on 2010-08-17
me parece que voy a optar por el script. 

si me surgen dudas les posteo. gracias por sus respuestas....

---

