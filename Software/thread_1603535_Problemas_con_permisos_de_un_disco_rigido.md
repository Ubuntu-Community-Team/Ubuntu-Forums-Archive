---
title: "Problemas con permisos de un disco rigido"
date: 2010-10-22
forum: Software
---

### Post by matias_tati on 2010-10-22
Hola que tal bueno tengo un disco rigido de 115g que hace poco formatee usando Windows Seven, la cosa es que desde linux no puedo copiar nada a dicho disco, ni crear enlaces de las carpetas del mismo, solamente lo puedo hacer desde Windows. Ayuda por favor.

---

### Post by guillermolisi on 2010-10-22
Le diste formato para que tipo de sistema de archivos, NTFS, FAT, otro ?

---

### Post by matias_tati on 2010-10-22
Ntfs

---

### Post by guillermolisi on 2010-10-23
No se si el sistema de seguridad de NTFS se ha modificado en Win7, pero podria ser la causa siempre que estes intentando acceder sin privilegios de superusuario y usando una version compatible con esa version de NTFS de NTFS-3g.

Lo podes montar ? Porque si no nunca podras accederlo.

---

### Post by juancarlospaco on 2010-10-23
[**Click aca**]("apt:/nautilus-gksu?refresh=yes")

Despues, anda al disco, 
hacele click derecho arriba del icono del disco
y usa la opcion de abrir como root.
:)

---

### Post by juancarlospaco on 2010-10-23
repetido :(

---

### Post by hectorivand on 2010-10-23
> **matias_tati said:**
> Hola que tal bueno tengo un disco rigido de 115g que hace poco formatee usando Windows Seven, la cosa es que desde linux no puedo copiar nada a dicho disco, ni crear enlaces de las carpetas del mismo, solamente lo puedo hacer desde Windows. Ayuda por favor.

Hola Matías, es un mamada que se pega cada tanto NTFS, pareciera que es más un tema de caprichos del sistema de archivo que de permisos. me ha pasado, la recomendación es que rescates lo que esta y con Gparted elimines la partición y la vuelvas a crear.

Por lo menos yo, en su momento no encontré forma valida para que me reconozca como "valido" para escribir en el disco sin antes hacer esto que te comento :D

Saludos
Nacho

---

### Post by hectorivand on 2010-10-23
> **juancarlospaco said:**
> [**Click aca**]("apt:/nautilus-gksu?refresh=yes")

Despues, anda al disco, 
hacele click derecho arriba del icono del disco
y usa la opcion de abrir como root.
:)

Hola Juan, perdón que te contradiga, pero cuando lo intentas hacer te tira un error de acceso denegado o parecido (no lo recuerdo textualmente). Intente de varias maneras "tomar" control del disco como root pero no hay caso.

Saludos
Nacho

---

