---
title: "Problema con actualizacion de Jaunty"
date: 2009-05-20
forum: Software
---

### Post by Tenisfan on 2009-05-20
Hola amigos, de nuevo recurro a su ayuda. Resulta que el gestor de actualizaciones de mi Ubuntu 9.04 de 64 bits me tira el siguiente error:
> No se pueden instalar las actualizaciones
An unresolvable problem occurred while calculating the upgrade:
E:No se pudieron corregir los problemas, usted ha retenido paquetes
rotos.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Probablemente sea un problema transitorio, inténtelo de nuevo más tarde.
Como puedo hacer para descubrir cual es el paquete que está en conflicto? Les cuento que instalé varias aplicaciones a traves de Getdeb y alguna otra pagina que ya tenía el .deb hecho, ¿cómo hago para desinstalar alguna aplicación de esas, o sea que no esta en agregar o quitar programas? 
Bueno, espero que puedan ayudarme otra vez, desde ya gracias, saludos!):P
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Hei Ku on 2009-05-20
Te podes fijar cuales son los paquetes rotos?

A partir de ahí, podes fijarte el error que te tira al tratar de instalar ese paquete. 

Generalmente, tiene que ver con un paquete que quiere escribir al mismo archivo, asi que tenes que desinstalar los dos, y despues volver a instalarlos (y supuestamente en la nueva version se arregla el conflicto)

Bueno, con eso tenes para empezar. Suerte!!!

Si las instalaste a traves de un .deb, entonces las tenes que tener en Synaptics.

---

### Post by Tenisfan on 2009-05-26
retomo el post despues de unos dias de descanso...Estoy casi seguro que el problema es con los paquetes de OPen Office, porque trate de instalar manualmente la version 3.1, entonces ahi se debe haber generado el problema. Ahora, como hago para eliminar todos los paquetes?

---

### Post by Hei Ku on 2009-05-26
sudo apt-get remove nombre-del-paquete

---

