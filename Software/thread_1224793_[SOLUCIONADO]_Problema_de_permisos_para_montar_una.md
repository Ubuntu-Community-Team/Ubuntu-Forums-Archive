---
title: "[SOLUCIONADO] Problema de permisos para montar una capeta via NFS"
date: 2009-07-27
forum: Software
---

### Post by krebscycle on 2009-07-27
Estimados.

Tengo el siguiente problema. 

He creado un carpeta llamada /mnt/buser que pertenece al usuario y al grupo "buser" y "beowulf" respectivamente. Esta carpeta la utilizo como punto de montaje. El problema es que la momento de montarla (vía NFS) esta cambia de propietario y de grupo, impidiemdome (por una cuestion de permisos) revisar el contenido de la misma.

¿Cómo puedo espeficiar el dueño y grupo de una carpeta montada vía NFS?.

---

### Post by jci on 2009-07-28
> **krebscycle said:**
> Estimados.

Tengo el siguiente problema. 

He creado un carpeta llamada /mnt/buser que pertenece al usuario y al grupo "buser" y "beowulf" respectivamente. Esta carpeta la utilizo como punto de montaje. El problema es que la momento de montarla (vía NFS) esta cambia de propietario y de grupo, impidiemdome (por una cuestion de permisos) revisar el contenido de la misma.

¿Cómo puedo espeficiar el dueño y grupo de una carpeta montada vía NFS?.

Postea :

- propietario/grupo del directorio mentado, despues que cambia de usuario/propietario (a que?)
- /etc/exports

Saludos,
--j

---

### Post by kamus on 2009-07-30
y tu /etc/fstab (si lo declaraste aqui para montar automaticamente la unidad claro heh).

Salu2:P

---

### Post by krebscycle on 2009-07-31
PROBLEMA RESUELTO

El problema consistía en que el *uid* (user id) del usuario "buser" y el *gid* (group id) del grupo "beowulf" que estaban asigandos en el primer equipo no eran iguales a los que estaban asignados al usuario "buser" y grupo "beowulf" del segundo equipo.

Por lo tanto, al montar la carpeta del primer equipo en el segundo, en este último se montaba bajo la propiedad de un *uid* y un *gid* que numéricamente correspondian a un tercer usuario, negandose de esta manera los permisos para acceder a su contenido por parte del usuario buser.

El problema fue resuelto creando un par de usuarios con el mismo nombre y grupo, así como teniendo cuidado en que los *uid* y *gid* también fueran iguales en los dos equipos.

Como referencia, los valores de *uid* y *gid* se pueden revisar en la herramienta gráfica de administración de usuarios y grupos de Ubuntu.

Saludos
Marcelo Rivas-Astroza

---

### Post by tony123 on 2010-03-30
También enfrentan el mismo problema pero se  resolvió de forma automática

---

### Post by hafiz123 on 2010-06-26
i am hafiz from pakistan and i have read all of your posts and i like  all of it.thanks for sharing such type data.now i am here  unintentionally.but next time i will be here for preparation and submit  something different for all of you people kindly wait for me.i ,ll miss  you all of you people.

---

