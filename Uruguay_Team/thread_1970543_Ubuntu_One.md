---
title: "Ubuntu One"
date: 2012-05-01
forum: Uruguay Team
---

### Post by francomariani on 2012-05-01
Hola para todos. Les comento que hace unos días instalé el ubuntu 12.04 desde cero, y comencé a instalar los software que siempre utilizo y a configurarlos.
Entre esas configuraciones, instalé el ubuntu one y conecté mi cuenta.
Luego, en las notificaciones me aparece que se están descargando los archivos pero en realidad sólo me descargó algunos. Tengo en total 1,3 gb de información pero tengo una buena conexión de internet que me debería haber descargado todo en menos de dos horas, y sin embargo sigue igual, sólo me descargó algunos archivos.
Me he desconectado y conectado de nuevo pero me pasa lo mismo. Y he dejado la notebook prendida por horas por las dudas pero nada..
Ni idea qué puede pasar que no me termina de descargar todo.
Así que bueno, cualquier ayuda me sirve, muchas gracias,
Saludos,
Franco.

---

### Post by cintiaarosales on 2012-05-23
Saludos Franco,
Hace un tiempo me encontré en una situación similar con los archivos de música que adquirí y baje a traves de mi cuenta en Ubuntu One. Recuerdo que en su momento encontré en uno de los cuantos Ubuntu forums que hay, una solución para mi caso. Aprendi dos cosas:
1.Se puede sincronizar carpetas solo en tu carpeta de inicio (sin importar si eres usuario de Ubuntu o de Windows).
2.En el ordenador desde el que se están sincronizando debes marcar la casilla de sincronización local después de agregar la carpeta, o de lo contrario solo se sincronizará la carpeta sin su contenido.

Para chequear el progreso de sincronización yo uso CLI:
```
u1sdtool --current-transfers
```
Para ver el numero de archivos a la espera de sincronizar y comprobar que metadatos de archivo esta siendo procesado, se puede utilizar:
```
u1sdtool --waiting | wc -l
```
Para chequear el estado del Ubuntu One, sugiero:
```
u1sdtool-s
```
Espero que la información haya sido útil, cuéntame al respecto :)
Cintia

---

### Post by francomariani on 2012-05-23
Hola Cintia, primero que nada, muchas gracias por responder. Vos sabés que hace poquitos días se me solucionó sólo el problema. Es decir, me terminó de descargar toda la información/ficheros desde la cuenta. Ya tenía configurado lo que me dijiste en el punto 2. No entendí mucho el punto 1, sobre todo a qué le llamas la carpeta de inicio, me imagino que será la carpeta home (carpeta personal de mi usuario más precisamente).
Igualmente está bueno tener en cuenta esos códigos que me pasaste para la terminal, por las dudas en un futuro. 
Como está solucionado voy a cambiar el título del post.
Saludos y gracias otra vez,
Franco.

---

