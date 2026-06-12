---
title: "Como puedo hacer para escribir un disco externo HFS+?"
date: 2009-06-21
forum: Software
---

### Post by DrKenobi on 2009-06-21
Hola: tengo un disco externo formateado para MacOS con el formato HFS+

Solo puedo leer (copiar archivos desde el disco externo a mi PC, pero no puedo copiar archivos desde mi PC al disco externo).

NO TENGO ESCRITURA!!!

Ya probe instalando todos los paquetes que incluyen hfs y nada, sigo en la misma.

Si alguno sabe algo, le agradezco me cuente un poco

Gracias

---

### Post by staar on 2009-06-21
linux soporta escritura en HFS+, pero con una condición, se debe desactivar el journaling en el sistema de archivos...

acá: [http://magarto.com/blog/archivo/2007/03/27/howto-montar-lecturaescritura-chequear-y-reparar-hfs-en-ubuntu/]("http://magarto.com/blog/archivo/2007/03/27/howto-montar-lecturaescritura-chequear-y-reparar-hfs-en-ubuntu/") hay un tutorial de como montar el FS (ojo que la desactivación del journaling se hace desde OSX, desconozco si puede hacerse desde GNU/Linux), requiere un poco de compilación y toqueteo, pero nada del otro mundo...

saludos

---

