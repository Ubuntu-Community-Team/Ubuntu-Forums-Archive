---
title: "KDE4.1 sobre Gnome: Error en plasma y PIM desactualizado"
date: 2008-08-09
forum: Software
---

### Post by GGsalas on 2008-08-09
Hola, no me aguanté a esperar la próxima version de Kubuntu y decidí instalar KDE 4.1 sobre mi Ubuntu. Primero me dio un error que no recuerdo y luego volvi a instalar y se completó (o al menos no dio error).

A veces Plasma da error (adjunto el archivo de error)

He descubierto que los programas de correo y agenda (PIM) no están actualizados, a pesar de que según veo en [KDE]("http://www.kde.org/announcements/4.1/"), se han actualizado.

A Amarok, lo tuve que instalar desde "añadir/eliminar programas" y se instaló la versión para KDE 3.

Por último, los check boxes que firefox muestra dentro de las páginas web, se ven con un desagradable fondo gris :P Nada preocupante, solo digo.

Quisiera algo de ayuda, aunque supongo que cuadno instale el próximo Kubuntu desde cero, va a funcionar todo bien. Gracias.

---

### Post by pol666 on 2008-08-09
> 
A veces Plasma da error (adjunto el archivo de error)

A mi tambien, era la version final? a mi me paso con un beta, reporta el bug por las dudas

> A Amarok, lo tuve que instalar desde "añadir/eliminar programas" y se instaló la versión para KDE 3.
Es que amarok esta hecho en QT3 no QT4


> 
Por último, los check boxes que firefox muestra dentro de las páginas web, se ven con un desagradable fondo gris :P Nada preocupante, solo digo.

Instalate un tema para firefox, FF en KDE se ve horrible

---

### Post by Hei Ku on 2008-08-09
Amarok2, la version para KDE4, esta en Alpha 2, asi que no viene en los repositorios. Lo mismo sucede con KOffice2, que está en Alpha 9.

En cuanto al FF, eso es porque toma el tema de KDE, seguramente está tomando el de KDE3, que debes tener configurado al default. Instalate kcontrol, y configurate un tema, con colores, etc. Despues de eso debería tomar esa configuración. En ese sentido, FF3 mejoró un poco de las versiones anteriores, que sólo tomaban el tema de GTK.

---

### Post by GGsalas on 2008-08-09
> **pol666 said:**
> A mi tambien, era la version final? a mi me paso con un beta, reporta el bug por las dudas

Instalé Kubuntu 4.1 en mi Ubuntu 8.04 actualizado por internet a la fecha. Tengo el archivo del bug, pero no se a donde debo enviarlo.

> Es que amarok esta hecho en QT3 no QT4

¿No hay version final de Amarok para KDE4? he visto un monton de capturas de la nueva version, pensaba que ya existía.

> Instalate un tema para firefox, FF en KDE se ve horrible

Lo hice, pero estoy usando una que imita a KDE4, probaré con otra.

Aviso que los programas PIM, los he logrado actualizar mediante la instalación de paquetes "a ojo" desde Synaptic. Nada recomendable, pero es lo que hice. Saludos.

---

### Post by Hei Ku on 2008-08-09
Para no repetir la mala experiencia con KDE 4.0, fijense que los blogs de los desarrolladores en general incluyen un disclaimer que explicita si lo que muestran es un alpha, beta o algo sobre lo que están trabajando todavía y no está siquiera en el repositorio común.

En el caso de Amarok, esto lo que dice la pagina oficial:
> 
Aulanerk - Alpha 2 of Amarok 2.0 released!
July 22, 2008 - 17:25 &#8212; nightrose

The Amarok team is proud to announce the second alpha version of Amarok 2, codenamed Aulanerk. We have spent many sleepless nights resolving issues and polishing features since the first alpha was released. It wasn't just for fun though ;-) We want the 2.0 release to be the best ever. 


---

### Post by pol666 on 2008-08-09
no amarok esta en alpha mas que inestable


A mi firefox se veia bien con el tema Oxygen que le puse  lo djee bien el KDE hasta que murio en un plasma crash

---

### Post by jpmorelli on 2008-08-10
En realidad ya esta la version de Amarok 2.o y está en los repositorios para poder instalarse en KDE4. El paquete es:

sudo apt-get install amarok-kde4

...pero como ya dijeron, es inestable, ni siquiera esta en beta.
Suerte !

---

### Post by GGsalas on 2008-08-11
Gracias, ya lo instalé y va bastante bien, sólo no debo poner algunos componentes en la sección central porque no funcionan bien, pero para lo que sirve: escuchar música, radio y podcast, va muy bien. 

¡Saludos!

---

