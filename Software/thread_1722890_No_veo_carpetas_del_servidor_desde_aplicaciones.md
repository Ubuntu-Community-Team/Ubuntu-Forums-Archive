---
title: "No veo carpetas del servidor desde aplicaciones"
date: 2011-04-06
forum: Software
---

### Post by ignacioguevara on 2011-04-06
Hola a todos:
Finalmente instale una pequeña red con un Ubuntu server 10.4 y 4 pc con Ubuntu 9.10.
Desde cada una de la pc's se accede a los archivos en carpetas del servidor mediante marcadores y a una carpeta compartida de cada una de ellas.
El problema que se me presenta es que en alguna de las aplicaciones no puedo acceder a carpetas del servidor.
Por ejemplo:
En una de las pc tengo conectado un pequeño scanner y cada vez que escaneamos un documento (usamos el programa ya instalado en Ubuntu, el Escaner de imagenes Xsane) lo tenemos que guardar en el disco local y una vez terminado el proceso debemos moverlo a la carpeta correspondiente del servidor. Y esto es así porque al momento de elegir donde se guarda el documento el programa no muestra los marcadores al server solo muestra las carpetas locales.
Lo mismo sucede cuando desde thundebird se quiere grabar un email como documento y dejarlo en una carpeta del servidor. Solo se muestran la opciones locales, por lo que hay que guardar a nivel local y despues hacer el pase
Hay alguna menera de solucionar esto?
Desde ya muchas gracias

Ignacio

---

### Post by aromo on 2011-04-06
Estas montando las carpetas del servidor en cada PC?  Si las estas montando, estas usando Samba o NFS?

---

### Post by ignacioguevara on 2011-04-06
Si las estoy montando?
si a lo que te referis es a algo asi como mount 192.168.0.10 ....
no no las monto asi
tengo samba instalada porque hay una notebook con windows vista.
lo que hice fue generar un marcador entrando por Lugares / Red / nombredel servidor / carpeta del servidor
una vez alli fui a Marcadores / Añadir Marcador
Si lo que debo hacer es otra cosa, bienvenido sea el dato

---

