---
title: "problemas con flash despues de actualizar"
date: 2011-11-12
forum: Software
---

### Post by drazhe on 2011-11-12
Hola comunidad! hoy al encender mi computadora me salta el cartel de que había actualizaciones disponibles y la única que había para instalar era una librería de flash (por desgracia no recuerdo bien el nombre pero era algo así como **libflash** o y creo que decía algo de adobe también) pues procedo a actualizar y funciono bien.. pero luego de reiniciar la PC, y querer entrar a youtube o a cualquier pagina con flash, me salta el cartel diciendo que falta el plugin y que hay que actualizarlo y todo eso. 
Pero cuando quiero hacerlo de manera manual, y descargarlo desde la pagina de adobe, me tira el siguiente error... 

[IMG]http://i41.tinypic.com/23limf6.png[/IMG]

Copio el texto de abajo porque sale cortado en la imagen..

"Imposible obtener [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  No pude conectarme a archive.canonical.com:80 (91.189.88.33). - connect (110: Expiró el tiempo de conexión)
Imposible obtener [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-es.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-es.bz2)  Imposible conectar a archive.canonical.com:http:
Imposible obtener [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Imposible conectar a archive.canonical.com:http:
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar."

hay manera de solucionar esto? y reinstalar flash sin mayores problemas? ni en chromium funciona correctamente el flash...

---

### Post by hictio on 2011-11-12
Qué versión de Ubuntu estás usando? Yo tengo Lucid Lynx 32 bits y vi la ventana de update a la mañana pero no hice el update todavía... Ahora al ver esto creo que lo voy a posponer?
El paquete se llama, según el updater "flahsplugin-installer".

---

### Post by drazhe on 2011-11-12
estoy usando ubuntu 10.04 lucid lynx y te recomiendo no lo actualices! desde entonces no me funciona flash...

---

### Post by drazhe on 2011-11-12
bueno, pude solucionar el tema, aunque aun no se que pudo haber pasado... 

la solucion que utilicé es hacer esto en un terminal

> **sudo dpkg --configure -a**

y luego reinstalar el plugin... una vez reiniciado firefox, todo funcionaba correctamente... 

Insisto en que aún no se que pudo haber pasado ya que la actualización de flash me salto desde el propio gestor de actualizaciones..

---

### Post by elcangrejoviajero on 2011-12-14
Hola!que tal?Hace una semana que estoy usando este SO y la verdad me usta mucho. ya ni quiero volver a Windows jeje. Bien. Yo también tengo ese problema con los videos en internet que no puedo verlo. Ya intentè hacer esos pasos pero sigo sin poderver los mismos. ¿Que puedo hacer? Tengo Ubuntu 8.04. Desde ya, muchas racias por su ayuda. Saludos

---

### Post by guillermolisi on 2011-12-14
> **elcangrejoviajero said:**
> Hola!que tal?Hace una semana que estoy usando este SO y la verdad me usta mucho. ya ni quiero volver a Windows jeje. Bien. Yo también tengo ese problema con los videos en internet que no puedo verlo. Ya intentè hacer esos pasos pero sigo sin poderver los mismos. ¿Que puedo hacer? Tengo Ubuntu 8.04. Desde ya, muchas racias por su ayuda. Saludos

Mi recomendacion es que actualices de version. La 8.04 se quedara sin soporte en unos meses. Ademas, este problema con 10.04 esta solucionado, asi que resolves dos cuestiones de una sola vez (salvo que tengas alguna razon en particular para no querer opoder actualizar la version de Ubuntu).

---

