---
title: "Error en Area de Notificacion Panel Superior"
date: 2010-06-10
forum: Software
---

### Post by RafaelG on 2010-06-10
[SIZE=4]Hola a todos los ubunteros de chile. Despues de un tiempo utilizando la version 10.4 LTS, mi unico inconveniente con el paso a la nueva version en mi notebook dell vostro 1510 es en el area de notificacion panel superior sale error en el icono de network manager dejo foto visualizando.
[/SIZE]

---

### Post by Carlos C on 2010-06-11
Me ha pasaba en Jaunty que ese ícono no se cargaba bien, me aparecía un cuadro negro. Lo que hice fue cambiar el tema de íconos y con eso se resolvió.

Saludos.

---

### Post by RafaelG on 2010-06-11
> **Carlos C said:**
> Me ha pasaba en Jaunty que ese ícono no se cargaba bien, me aparecía un cuadro negro. Lo que hice fue cambiar el tema de íconos y con eso se resolvió.

Saludos.

[SIZE=3]
Carlos C,

No habria alguna solucion para correguir el error del icono desde consola o desde repositorios?
[/SIZE]

---

### Post by flakojaime on 2010-06-14
Rafael.

A mi me paso algo parecido, el network manager se desaparecio de la barra al instalar algunas actualizaciones en el 10.4.



:popcorn::popcorn:

---

### Post by Carlos C on 2010-06-14
Tengo una duda, ¿esto ocurrió después de actualizar de Karmic a Lucid o se dio en una instalación limpia de 10.04?

En caso de haber sido una actualización, ¿qué versión de update-manager tienen?

Les recomiendo mirar aquí por si tiene relación con el problema:

[https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager-applet/+bug/456468](https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager-applet/+bug/456468)

Saludos.

---

### Post by RafaelG on 2010-06-15
> **Carlos C said:**
> Tengo una duda, ¿esto ocurrió después de actualizar de Karmic a Lucid o se dio en una instalación limpia de 10.04?

[SIZE=3]Carlos, 

Realize una instalacion en Limpio pero con la ultima version Beta de Lucid, por lo que estuve leyendo en Launchpad al parecer fue un bug del nm-applet de la version beta, ahora por lo que explican al salir el released definitivo de lucid en el gestor de actualizaciones se realizaria una descaga para dejar el usr/bin/nm-applet definitivo de la version el cual debiera solucionar el problema pero al parecer yo no lo he recibido o algo paso por que ya realize todas las actualizaciones que me ha solicitado el gestor y lo tengo sin nada pendiente.
[/SIZE]

---

### Post by renzo.martinez.friz on 2010-06-21
Estimados:

Discúlpenme, por favor, si "meto la cuchara" donde no se debe, pero tengo un problema parecido (si se debe crear otro tema, por favor, corríjanme).  El área de notificaciones últimamente está cambiando los íconos repitiendo unos y ocultando otros, por ejemplo, repite dos veces el ícono de sonido, pero elimina el de wifi; repite el de conectividad del usuario y elimina el botón para apagar (lo que me obliga a instalar un botón de "Apagado" para poder cerrar el equipo).

La instalación se hizo a partir de una copia descargada completamente de 10.04 (no una actualización desde 9.10), previo formateo del equipo y sin ninguna intervención de eliminación de archivos como me ocurrió la vez anterior.

¿Tendrá que ver con un error del sistema, considerando que RafaelG tiene también con problemas de notificación?  (Esto me ocurre con un NB Compaq).

Saludos.

Renzo Martínez Friz.

---

### Post by Carlos C on 2010-06-23
supuestamente ese problema se arregló a partir de update-manager - 1:0.134.9 ¿Qué versión tienen ustedes?

---

### Post by flakojaime on 2010-06-27
como veo la version del update manager?

---

### Post by RafaelG on 2010-06-28
> **Carlos C said:**
> supuestamente ese problema se arregló a partir de update-manager - 1:0.134.9 ¿Qué versión tienen ustedes?


[SIZE=2]Carlos C,

Es la version que tengo yo instalada, ahora estuve viendo por el lado de los Theme y por el momento cambiando de Theme he solucionado el inconveniente temporalmente pero eso no quiere decir que se solucione el problema por completo. yo seguire investigando en Google y los diferentes foros a ver si hay alguna solucion por completo.

[/SIZE]


> **flakojaime said:**
> como veo la version del update  manager?[SIZE=2]
Flakojaime,

Una forma muy facil de ver la version que tienes instalada es en el Ubuntu Software Center con la siguiente direccion: Aplicaciones/Ubuntu Software Center. En el cuadro superior donde dice busqueda pones el nombre del software que quieres ver  y te despliega la informacion de los diferentes Software que tienes instalados en tu OS.[/SIZE]

---

### Post by flakojaime on 2010-06-29
> **RafaelG said:**
> [SIZE=2]

  ...los Theme y por el momento cambiando de Theme he solucionado el inconveniente temporalmente....
[/SIZE]  [SIZE=2].[/SIZE]

Rafael, cual es el tema que pusiste?, he cambiado varios y no logro recuperar, tengo la misma version del update.

gracias!

---

### Post by RafaelG on 2010-06-29
> **flakojaime said:**
> Rafael, cual es el tema que pusiste?, he cambiado varios y no logro recuperar, tengo la misma version del update.

gracias!

[SIZE=2]Flakojaime,

Tienes que cambiar el tema del icono pero repito es una solucion temporaria, no es definitiva!
[/SIZE]

---

### Post by RafaelG on 2010-07-15
[SIZE=2]El problema continua sin poder conseguir una solucion definitiva. si alguien tiene mayor informacion de como solucionar el inconveniente estare atento a sus comentarios.[/SIZE]

---

### Post by themasterdark on 2010-07-15
El problema de RafaelG tiene que ver mas con el despliegue de la imagen asociada a ese icono. Por ello se "arregla" al cambiar el tema de los iconos.


El de Flako... viene mas a mi parecer por los applets que estan agregados en el panel, lo mas sensato que haria sería:

Borrar todos los applets, applet-indicator, nm-applet, etc..

y volver a colocarlos de uno en uno.


como se borran:

boton derecho sobre el applet -> borrar


como se vuelven a colocar:

boton derecho en el panel de gnome -> añadir

desde ahi muestra una lista con todos los applets eligen los que quieran colocar y vee como te va


Saludos!

---

### Post by RafaelG on 2010-07-17
> **themasterdark said:**
> El problema de RafaelG tiene que ver mas con el despliegue de la imagen asociada a ese icono. Por ello se "arregla" al cambiar el tema de los iconos.

Themasterdark,

Si ya estaba alto del cambio del theme del icono Gracias, pero como lo habia indicado es una solucion parche por que no soluciona el problema de raiz con el theme que viene por default con la version 10.4 LTS.

---

