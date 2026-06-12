---
title: "Juego de truco"
date: 2008-08-03
forum: Software
---

### Post by ramiro_md on 2008-08-03
Gente llevo dias buscando algun juego de truco para ubuntu pero no encuentro =s. Se que debe haber, si alguien tiene digamelo de donde lo obtuvo plizzz :)..UN saludo !

---

### Post by ubuntu27 on 2008-08-03
A que te refieres con juego de truco?

Juegos que te hacen pensar? 


Si es asi te recomiendo **enigma**, esta en el repositorio.
Tienes que mover la bola con el mouse y completar los niveles y mundos. Hay miles de niveles con distintos objetivos (que tu mismo tienes que encontrar).

---

### Post by luchardi on 2008-08-03
Me imagino que se refiere al juego de Truco, el juego nacional de truco con naipes (cartas)

Te dejo un link si es lo que estas buscando seguro te va a venir bien:

[http://truco4linux.iespana.es/](http://truco4linux.iespana.es/)

---

### Post by ramiro_md on 2008-08-03
> **luchardi said:**
> Me imagino que se refiere al juego de Truco, el juego nacional de truco con naipes (cartas)

Te dejo un link si es lo que estas buscando seguro te va a venir bien:

[http://truco4linux.iespana.es/](http://truco4linux.iespana.es/)

Tal cual, era eso lo que buscaba ! =)

---

### Post by juanman on 2008-08-04
Yo juego siempre al [truco de taringa]("http://www.taringa.net/juegos/truco/"). Es online, necesitas java.
Esta muy bueno, se puede chatear mientras se juega. Hay q registrarse, pero es gratis...

Saludos

---

### Post by Mauro22 on 2009-01-29
Muchachos y Muchachas!



Revivo este topic para comentarles que decidi seguir con este proyecto del truco, truco4linux, cuya direccion esta arriba. La version que esta es la Aplha desarrollada por su autor y segun el changelog es del 2006.

Intente comunicarme con el autor, pero el mail ya no existe, asi que ojala lo encuentre a traves de este foro.



Bue sin mas, les dejo el proyecto actualizado a gambas2, con un par de cosas de mas. Sigue siendo alpha, pero lo dejo por si alguien quiere sumarse... No se si estoy violando alguna regla del open source a plublicar algo que no me pertenece, pero no puedo contactar al autor. 



[Truco4Linux]("http://truco4linux.iespana.es")
Desarrollado por Christian Santamaria


Les dejo el deb y el source en tar.gz en rapidshare, porque supera el limite del foro.


:arrow:[http://rapidshare.com/files/191297678/truco_0.0.7-1_all.deb.html](http://rapidshare.com/files/191297678/truco_0.0.7-1_all.deb.html)
:arrow:[http://rapidshare.com/files/191299056/truco-0.0.8.tar.gz.html](http://rapidshare.com/files/191299056/truco-0.0.8.tar.gz.html)

---

### Post by infernus92 on 2009-01-31
gracias mauro22... yo habia visto el juego en el link de mas arriba y me puse a bajarlo... pero esta en formato .tar.gz y yo no se armar los paquetes... ahora estoy bajando tu version en .deb
Espero que este bueno!!!!

---

### Post by lega on 2009-02-01
el paquete .deb me tira un error de dependencias **gambas2-gb-sdl-sound**
estoy usando Intrepid, tengo que agregar algún repositorio?

---

### Post by Mauro22 on 2009-02-01
La verdad que no se, yo tengo instalado gambas pero como vi la opcion de generar .deb pense que incluia todo...

Synaptic me tira esto:

```

mauro@ubuntu:~$ sudo apt-cache search sdl-sound
[sudo] password for mauro: 
libsdl-sound1.2 - Decoder of several sound file formats for SDL
libsdl-sound1.2-dev - Development files for SDL_sound
mauro@ubuntu:~$ 


```

Proba instalandolos

---

### Post by josecuervo86 on 2009-02-21
> **Mauro22 said:**
> Muchachos y Muchachas!



Revivo este topic para comentarles que decidi seguir con este proyecto del truco, truco4linux, cuya direccion esta arriba. La version que esta es la Aplha desarrollada por su autor y segun el changelog es del 2006.

Intente comunicarme con el autor, pero el mail ya no existe, asi que ojala lo encuentre a traves de este foro.



Bue sin mas, les dejo el proyecto actualizado a gambas2, con un par de cosas de mas. Sigue siendo alpha, pero lo dejo por si alguien quiere sumarse... No se si estoy violando alguna regla del open source a plublicar algo que no me pertenece, pero no puedo contactar al autor. 



[Truco4Linux]("http://truco4linux.iespana.es")
Desarrollado por Christian Santamaria


Les dejo el deb y el source en tar.gz en rapidshare, porque supera el limite del foro.


:arrow:[http://rapidshare.com/files/191297678/truco_0.0.7-1_all.deb.html](http://rapidshare.com/files/191297678/truco_0.0.7-1_all.deb.html)
:arrow:[http://rapidshare.com/files/191299056/truco-0.0.8.tar.gz.html](http://rapidshare.com/files/191299056/truco-0.0.8.tar.gz.html)

Cuando quise bajar el deb me salio esto:

Error

This file is neither allocated to a Premium Account, or a Collector's Account, and can therefore only be downloaded 10 times.

This limit is reached.

To download this file, the uploader either needs to transfer this file into his/her Collector's Account, or upload the file again. The file can later be moved to a Collector's Account. The uploader just needs to click the delete link of the file to get further information.

Resumiendo, lo alojaste en un cuenta privada (?) y solo se puede bajar 10 veces. Para poder seguir bajandolo tenes que volver a subirla o moverla ;)

---

### Post by sartrejp on 2009-02-21
Hey, convertí el tar.gz con alien, lo instalé y no me apareció en el menú. ¿Con que lo lanzo desde al terminal a ver que error me da?

---

### Post by fausto_w on 2009-04-29
Alguien que lo pueda subir a otro servidor? el de rapidshare no funciona..

---

### Post by fausto_w on 2009-04-29
> **fausto_w said:**
> Alguien que lo pueda subir a otro servidor? el de rapidshare no funciona..
..todavia estaba en la pag original del proyecto, [http://truco4linux.iespana.es/](http://truco4linux.iespana.es/)
pero el codigo fuente no esta :/

Estoy tratando de hacerlo multiplayer, alguien que me tire una idea de por donde empezar? Java mas o menos básico es lo que se, y hace como un año que no programo en gral, por eso pregunto.

Ideas por favorrr =) ?

---

