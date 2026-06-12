---
title: "No arranca"
date: 2009-11-23
forum: Software
---

### Post by federicoand on 2009-11-23
Luego de actualizar a ubuntu 9.10 luego de dos meses no me arranca.- Me tira el siguiente error:

failed to spawn mountall-shell post-stop process: unable to execute: permission denied

job_process c:529: unhandled error from job_process_spawn: Permission denied

y ahí queda.- Estuve buscando los errores por Internet y parece que a nadie se les había presentado.-

Alguna sugerencia?

---

### Post by alfplayer on 2009-11-23
Parece un problema nuevo. En un foro brasilero apareció ese error a alguien que modificó el archivo fstab (si no entendí mal). También hay alguien que tiene este error en [http://ubuntuforums.org/showthread.php?t=1335242](http://ubuntuforums.org/showthread.php?t=1335242) (en inglés) que además tiene problemas montando el sistema de archivos.

Como lo recomendé en el hilo en inglés recomiendo hacer un chequeo de integridad del sistema de archivos (antes se puede buscar si aparece error montando el sistema de archivos en /var/log/syslog ).

---

