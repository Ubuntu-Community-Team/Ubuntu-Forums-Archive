---
title: "Montar memoria sd celular"
date: 2009-11-06
forum: Software
---

### Post by sitiomatic on 2009-11-06
Hola, tengo un celu nuevo que ya paso dos meses en servicio tecnico. Hoy por fin me lo devolvieron.
El tema es que le estuve copiando cosas en la memoria sdhc y todo bien.
Al rato decidi copiar algo mas y me sale que no puede copiarlo porque no tengo permisos, insisti mil veces y nunca tengo permisos,me dice que la memoria es de solo lectura :shock:
Ante la duda, y antes de escribir aca (no se si el problema es ubuntu o el fono) me fui a otra maquina que tengo con win y trate de grabar algo y ningun problema o se que ubuntu se chiflo y ahora lo monta de solo lectura.
El so es karmic.
Que puedo hacer?
Grazzie!!

---

### Post by pablo.s on 2009-11-06
> **sitiomatic said:**
> Hola, tengo un celu nuevo que ya paso dos meses en servicio tecnico. Hoy por fin me lo devolvieron.
El tema es que le estuve copiando cosas en la memoria sdhc y todo bien.
Al rato decidi copiar algo mas y me sale que no puede copiarlo porque no tengo permisos, insisti mil veces y nunca tengo permisos,me dice que la memoria es de solo lectura 

A veces ese problema se
soluciona formateando la
tarjeta desde el mismo telefono.
Luego copias el contenido
otra vez.

---

### Post by sitiomatic on 2009-11-06
No please, debe haber otra opcion. La tarjeta es nueva y esta es la quinta vez que instalo todo!!
Copie todo a esta tarjeta desde ubuntu, dijo basta cuando quise volver a copiar otras cosas.
Ademas en win graba bien, el tema es de como la monta ubuntu.

---

### Post by pablo.s on 2009-11-06
La tarjeta la lee desde un
lector de tarjetas o conectando
el telefono con cable USB?

---

### Post by sitiomatic on 2009-11-06
El fono por usb en modo almacenamiento masivo.

---

### Post by pablo.s on 2009-11-06
Podés probar: 

-Copiando los archivos como
superusuario.
-Cambiar como superusuario
los permisos a escritura (aunque
sea para tu usuario)
-Montando la tarjeta desde un
lector de tarjetas.

Si no obstante todo esto no te dá
ningún resultado, vemos si llega
a postear alguien alguna sugerencia.

---

### Post by sitiomatic on 2009-11-07
Lo de superusuario no tiene mucho sentido, yo soy el owner de los archivos y carpetas y tengo full rights.
Encontre que la carpeta .Trash de la SD estaba corrupta, al punto de no saber si es un archivo o un dir.
No se porque windows ignora ese problema y copia igual mientras que ubuntu deja toda la tarjeta de solo lectura.
Ya backupee la tarjeta, formatee y ahora funciona normal.
Hay algun modo de arreglar eso sin formatear? 
Ahora estoy usando la opcion Expulsar de modo seguro, pero siempre me sale un cartel con un error que no se que es.
Hay algun modo seguro de montar / desmontar el fono?
Grazzie

---

### Post by guillermolisi on 2009-11-07
> **sitiomatic said:**
> Lo de superusuario no tiene mucho sentido, yo soy el owner de los archivos y carpetas y tengo full rights.
Encontre que la carpeta .Trash de la SD estaba corrupta, al punto de no saber si es un archivo o un dir.
No se porque windows ignora ese problema y copia igual mientras que ubuntu deja toda la tarjeta de solo lectura.
Ya backupee la tarjeta, formatee y ahora funciona normal.
Hay algun modo de arreglar eso sin formatear? 
Ahora estoy usando la opcion Expulsar de modo seguro, pero siempre me sale un cartel con un error que no se que es.
Hay algun modo seguro de montar / desmontar el fono?
Grazzie
Si lo que se monta es la tarjeta de memoria del telefono como si fuera un pendrive, con mount/umount (y los parametros correspondientes) deberia funcionar lo que pretendes (que basicamente es lo mismo que hace el sistema cuando indicas desmontar desde el entorno grafico con la diferencia de que un comando en consola normalmente brinda algo mas de informacion, sobre todo cuando algo no anda bien).

---

### Post by biale on 2009-11-07
Les cuento que dando vueltas por mi casa hay mp3 y un mp4, ambos de marca reconocida. Y también han aparecido problemas al borrar o quizas guardar archivos, desde ubuntu, en modo "almacenamiento masivo".

Sospecho que la implementación del sistema de archivos en estos aparetejos no sigue al pie de la letra las especificaciones. Y desde luego, usando a diario un auténtico pen drive nunca tuve ningún problema.

Con la cámara fotográfica tampoco aparecieron problemas. 

Saludos.

---

