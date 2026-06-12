---
title: "Problema con la actualización de Ubuntu 12.04"
date: 2014-01-27
forum: Software
---

### Post by lucasdelavega on 2014-01-27
Hola a todos,
Soy muy ignorante aunque muy amante de Ubuntu y estoy teniendo un problema que no puedo resolver al querer hacer actualizaciones a través del gestor de actualizaciones. 
Desde hace ya un par de meses no puedo terminad de hacer actualizaciones porque me tira le siguiente error:

[COLOR=#000000][FONT=Helvetica] [/FONT][/COLOR](Reading database ... 50%%dpkg: unrecoverable fatal error, aborting: files list file for package `libxxf86vm1' contains empty filename
Error in function: 

Cualquier información, la voy a agradecer mucho.
Gracias a todos

---

### Post by rolcamus on 2014-01-27
Hola, ¿has intentado con el Gestor de paquetes Synaptic?
Si no lo tienes puedes instalarlo desde el Centro de Software, y luego de instalarlo, hacer clic en "recargar", esperar a que busque las actualizaciones y luego "marcar todas las actualizaciones", seguido "aplicar" y ves que tal te va. Lo uso bastante cuando instalo una version beta de Ubuntu y funciona cuando el gestor de actualizaciones falla.
Suerte.

---

### Post by gildardo on 2014-01-27
El paquete que mencionas `libxxf86vm1' lo estás bajando de algún repositorio en línea? O es un paquete en algún tipo de medio -- CD, DVD, memoria USB? Es posible que el paquete esté corrompido, o que tenga algún error en el repositorio o espejo de donde lo estás tomando -- si lo último es el caso, quizá cambiando o agregando otro repositorio podrías obtener un paquete con todos los archivos (o ficheros, no sé cómo les llamen en Argentina) completos...

---

