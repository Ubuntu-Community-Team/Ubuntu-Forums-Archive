---
title: "Problema con el inicio: Ya existe un servidor X en ejecución en la pantalla 0"
date: 2009-08-31
forum: Software
---

### Post by cottita on 2009-08-31
Oliii :) ayer tuve varios problemillas para instalar Ubuntu 9.04
finalmente logré hacerlo
peeeero al iniciar, primero me dice que Ubuntu está funcionando en "Low Graphics Mode"
eso es muy probable que sea por mi tarjeta de video que es sólo una VIA que venía integrada en mi placa Madre... mi pc es un Olidata, Pentium 4 de 2.93 GHz, con 1GB de RAM, y en realidad todo lo que trae es integrado, quizás tb es un problema de compatibilidad de drivers.

Ahora luego de decirme que Ubuntu está funcionando en modo Low Graphics
tira un pantallazo azul  como el de la BIOS que dice:

Ya existe un servidor X en ejecución en la pantalla O: Desea intentar otro Nº de pantalla? Si responde No, GDM volverá a intentar iniciar el servidor en O: otra vez.

si uno elige No... tira la pantalla azul por toda la eternidad
si uno elige Si, sale una ventana en donde dice que Ubuntu se iniciará en el servidor 1: y uno puede dar en aceptar; por lo menos sale unas 3 veces esa ventana, antes de llegar finalmente a poder poner el Usuario y Contraseña... y luego Ubuntu funciona sin ningún problema ^^

any idea de cómo arreglarlo? :confused:

gracias de antemano

---

### Post by Carlos C on 2009-08-31
Hola. Prueba con el siguiente comando en el terminal:
```
dpkg-reconfigure gdm
```
Veamos si con eso se arregla. Respecto a la baja resolución, eso tendrías que verlo en un thread aparte (pero te adelanto que ese tipo de tarjetas no tiene buenos resultados en linux).

Movido al subforo "Software".
Saludos!

---

### Post by cottita on 2009-08-31
muchas gracias ^^
mmmm ahora entendí... es una consulta por thread
disculpen si no posteo donde corresponde
soy nuevita en esto...

gracias Carlos C, veré cómo me va con tu sugerencia!!

---

### Post by Carlos C on 2009-09-01
> **cottita said:**
> muchas gracias ^^
mmmm ahora entendí... es una consulta por thread
disculpen si no posteo donde corresponde
soy nuevita en esto...

gracias Carlos C, veré cómo me va con tu sugerencia!!

No hay problema. Cuando tengas dudas puedes mirar aquí:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos!

---

