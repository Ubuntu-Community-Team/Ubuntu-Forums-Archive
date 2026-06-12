---
title: "Error al intentar instalar Ubuntu"
date: 2011-05-13
forum: Software
---

### Post by El_canaya on 2011-05-13
Hola gente!!! despues de 3 años vuelvo por mi revancha en ubuntu (a ver si esta vez me me engancho jeje)

baje el cd de Ubuntu (ubuntu-11.04-desktop-i386), grabe el ISO en un cd, configuere para bootear desde el cd, pero cuando tendria que leerlo no lo lee y me aparece “DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER”... ya probe bootear el cd de windows (este si lo leyo) y tambien grabe de nuevo el cd de ubuntu pero tengo el mismo problema :S
ademas probe desde la opcion de windows "demostracion e instalacion total - necesito ayuda para arrancar desde el cd" pero en el ultimo segundo del asistente me aparece una ventana de error con lo siguiente: 
"ocurrio un error: 
Permission denied 
para mas informacion vea el archivo de registro: c:\ ... wubi-11.04-rev211"

alguna idea para solucionar esto?
realmente estoy interesado en pasarme esta vez a Ubuntu pero al perecer estoy empezando con el pie izquierdo jeje

Saludos!

---

### Post by biale on 2011-05-14
Pareciera que el CD quedo mal grabado. Lo mas correcto sería (1) chequear que la ISO haya bajado bien (el programa md5sum existe para Windows) y recien luego (2) grabar el CD con la opción de "verificar lo grabado". Y si el CD por lo menos arranca, dentro del menu existía la opción para verificar los contenidos.

Si hubiera un problema incipiente en la grabadora aparecería primero al usar las funciones de grabación y recien despues en las funciones de lectura. Incluso algunos tipos de lectura y no todos.

---

### Post by El_canaya on 2011-05-14
> **biale said:**
> Pareciera que el CD quedo mal grabado. Lo mas correcto sería (1) chequear que la ISO haya bajado bien (el programa md5sum existe para Windows) y recien luego (2) grabar el CD con la opción de "verificar lo grabado". Y si el CD por lo menos arranca, dentro del menu existía la opción para verificar los contenidos.

Si hubiera un problema incipiente en la grabadora aparecería primero al usar las funciones de grabación y recien despues en las funciones de lectura. Incluso algunos tipos de lectura y no todos.

gracias por rersponder!!
use este programa para ver los del md5sum: [http://www.md5summer.org/](http://www.md5summer.org/) y al parecer estaba bien descargado, tambien verifique lo grabado y me dio todo OK, pero sigo sin poder bootear el cd :S 
y la grabadora funciona porque si me lee otros cds y bootea el cd de windows...

alguna otra idea para solucionarlo? no puedo bootear desde un pendrive o dvd porque mi bios con tiene esas opciones

saludos!

---

### Post by biale on 2011-05-14
Dijiste "al parecer". La checksum verifica por igual o distinta, no hay termino medio.

El mensaje de boot failure lo da el BIOS. Lo unico que se me ocurre facil, es probar el arranque desde cualquier otra computadora, como para descartar mejor problemas en la copia del CD. 

Otra posibilidad sería probar con un CD de 10.10 Maverick...

---

### Post by El_canaya on 2011-05-16
al final baje la version 10.04.2 y lo pude instalar sin problemas :)

---

### Post by gyser on 2011-05-18
Bueno, tengo un problema similar pero generado por otra causa.  El asunto es que tengo un RAID 5 de 6 discos que dejo de acceder debido a que hice cambios en el hardware.
 
Estoy intentando ahora reinstalar Ubuntu, en el nuevo hard, con el cd de booteo que tengo preparado pero a mitad del proceso se cuelga el mismo y deja de avanzar...
 
Tengo mucha informacion importante que no esta respaldada y necesito acceder nuevamente.  EL tema es que si no lo logro voy a tener que acudir a un laboratorio de recuperaciones (Onretrieval es uno que me han mencionado) con el coste que supone ese tipo de servicios...
Quisiera que me brindaran algunas pistas de como proceder con algunas pruebas que pueda hacer, antes de pasar a esa decicisio...
 
Gracias.

---

### Post by El_canaya on 2011-05-20
gyser, capaz que te conviene abrir un nuevo tema porque este ya lo marcaron como solucionado y tal vez ni lo leen

saludos!

---

### Post by z37a on 2011-05-22
> **gyser said:**
> Bueno, tengo un problema similar pero generado por otra causa.  El asunto es que tengo un RAID 5 de 6 discos que dejo de acceder debido a que hice cambios en el hardware.
 
Estoy intentando ahora reinstalar Ubuntu, en el nuevo hard, con el cd de booteo que tengo preparado pero a mitad del proceso se cuelga el mismo y deja de avanzar...
 
Tengo mucha informacion importante que no esta respaldada y necesito acceder nuevamente.  EL tema es que si no lo logro voy a tener que acudir a un laboratorio de recuperaciones (Onretrieval es uno que me han mencionado) con el coste que supone ese tipo de servicios...
Quisiera que me brindaran algunas pistas de como proceder con algunas pruebas que pueda hacer, antes de pasar a esa decicisio...
 
Gracias.

Por favor gyser, abrí un nuevo tema así respondemos, por lo pronto este tema ya esta solucionado, por tu problema que es completamente distinto a este te recomiendo abras un nuevo tema!

---

