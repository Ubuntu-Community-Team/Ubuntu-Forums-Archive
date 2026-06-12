---
title: "problemas para acceder a papelera"
date: 2013-03-09
forum: Software
---

### Post by maximo68 on 2013-03-09
Tengo problémas a veces para vaciar y ver el contenido de la  papelera de reciclaje. Tambien pasa a veces con la carpeta personal. No se si el sistema de archivos esta dañado o que. 
saludos :confused:

---

### Post by guillermolisi on 2013-03-10
Mi sugerencia:

Verificar el estado del disco rigido con alguna herramienta afin y en modo no destructivo, despues de ver que informacion se ha recolectado sobre esa unidad via S.M.A.R.T.

Si S.M.A.R.T. no arroja errores en la unidad y la verificacion del estado del disco tampoco, verificar el estado de la particion que aloja a /home con fsck.

Si todas estas operaciones resultan satisfactorias y aun persisten los problemas, crear un nuevo usuario y verificar si con el tambien ocurren.
Si no sucede lo mismo, entonces hay algun problema de permisos o algun archivo de configuracion del usuario original no esta bien.

---

### Post by maximo68 on 2013-03-10
El SMART da sano. Si ejecuto fsck dice que la unidad montada puede ser dañada, googleando hay gente que dice perder datos

---

### Post by guillermolisi on 2013-03-10
Es que cualquier tarea de revision sobre una particion debe hacerse sin que esta este montada, usando una sesion Live desde un USB/CD.
Siempre es bueno contar con un backup. Nunca se sabe.

---

### Post by maximo68 on 2013-03-10
Tenes razon es un problema de permisos con los usuarios. Cree un invitado la reinicie. Hay me dejo acceder a la papelera y otros particiones.
SE AGRADECE MAESTRO.

---

