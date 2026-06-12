---
title: "Desmontar Unidad Externa"
date: 2010-06-09
forum: Software
---

### Post by prostata on 2010-06-09
Estoy observando en lucid, que al conectar un disco externo Matrox vía USB, al querer desmontarlo para extraerlo con seguridad, Lucid me envía un mensaje de error, del tipo, no se puede extraer la unidad.

Con karmic no me pasaba, y también observo que no existe en nautilus la opción Desmontar,al clicar sobre extraer también me manda error....

¿cómo solucionarlo...? tengo miedo de perder los datos del Disco externo, si lo saco a la brava.
Saludos

---

### Post by asterix77 on 2010-06-09
Usa la consola para determinar porqué no se puede desmontar

#sudo umount  /media/unidad

El resultado pégalo acá

También puedes forzar el desmontaje de la unidad de la siguiente forma

#sudo umount -l /dev/xxx

Sin embargo lo mejor es averiguar el tipo de error por el cual no se desmonta la unidad, lo más probable es que haya algún proceso que use la unidad. Para averiguarlo debes escribir

#fuser -vm /dev/xxx

Luego debes matar dichos procesos.

Espero te sirva

Saludos

---

