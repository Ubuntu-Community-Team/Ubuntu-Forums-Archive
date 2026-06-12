---
title: "[SOLVED] No abre songbird"
date: 2009-07-24
forum: Software
---

### Post by matias_tati on 2009-07-24
Hola que tal soy nuevo en ubuntu y las dudas parecen no tener fin.
Hize la reinstalacion de ubuntu 9.04 y logre recuperar los efectos del compiz que me faltaban. pero tuve que reinstalar songbird tmbn y que paso? Lo instalo como lo hize la primera vez, le doy al archivo y nunca se abre, me baje un .deb lo instalo todo perfecto y tampoco se abre y cando lo inmtento abrir nuevamente me tira un cartel, pero nunca se inicia. No se que estara pasando es el reproductor que mas me gusta. Gracias.

---

### Post by aledruetta on 2009-07-24
¿Haciendo click con el botón derecho, no te da una opción de abrir con el programa que maneja los paquetes .deb (GDebi)?

---

### Post by matias_tati on 2009-07-24
.........................................................

---

### Post by aledruetta on 2009-07-24
Ah, entonces está instalado. A mí me pasó eso una vez. Creo que fue cuestión de reiniciar el sistema nomás.

---

### Post by matias_tati on 2009-07-24
> **aledruetta said:**
> ¿Haciendo click con el botón derecho, no te da una opción de abrir con el programa que maneja los paquetes .deb (GDebi)?

Disculpame pero en donde deberia hacer click derecho pq ahora tengo instalado el paquete deb y en todo caso con que programa deberia abrirlo.

---

### Post by matias_tati on 2009-07-24
> **aledruetta said:**
> Ah, entonces está instalado. A mí me pasó eso una vez. Creo que fue cuestión de reiniciar el sistema nomás.
Si yo pense lo mismo pero ya reinicie mil veces y nada.

---

### Post by aledruetta on 2009-07-24
> **matias_tati said:**
> Disculpame pero en donde deberia hacer click derecho pq ahora tengo instalado el paquete deb y en todo caso con que programa deberia abrirlo.

No, disculpame, yo te malinterpreté, pensé que no podías abrir el paquete .deb.

---

### Post by matias_tati on 2009-07-24
La verdad no entiendo nada en lugar de reiniciar apague y prendi mi pc nuevamente y como arte de magia empezo a funcionar mil gracias igual...

---

### Post by aledruetta on 2009-07-24
Si vuelve a ocurrir, algo que podés intentar es, en la Terminal:
```
top
```
o
```
pgrep songbird
```
y, con el número de proceso que corresponde al Songbird:
```
kill xxxx
```
donde xxxx es el número de proceso
o bien:
```
pkill songbird
```
De esa manera cerrás el proceso y volvés a ejecutar la aplicación.

---

### Post by matias_tati on 2009-07-24
Muchisimas muchisimas gracias me emociona saber que hay tanta gente con ganas de ayudar, espero poder hacerlo yo en un futuro tmbn. Saludos!

---

### Post by NickCis on 2009-07-24
En la pagina de get deb te dicen que en los equipos con placas de video nvidia, vas a tener que desinstalar los singuientes paquetes para el correcto funcionamiento: libvisual-0.4-plugins
"sudo apt-get autoremove --purge libvisual-0.4-plugins"

[http://www.getdeb.net/release.php?id=4460](http://www.getdeb.net/release.php?id=4460)

Saludos.

---

### Post by Fire_C10 on 2009-08-05
Hola!, tengo ubuntu 9.04 e instale songbird 1.2, pero resulta que no inicia el programa aunque haya desistalado libvisual-0.4-plugins (aunque tengo una placa ATI).

¿Alguien me puede ayudar?

Saludos.

---

### Post by guillermolisi on 2009-08-05
> **Fire_C10 said:**
> Hola!, tengo ubuntu 9.04 e instale songbird 1.2, pero resulta que no inicia el programa aunque haya desistalado libvisual-0.4-plugins (aunque tengo una placa ATI).

¿Alguien me puede ayudar?

Saludos.
Probaste de abrir una terminal/consola e invocar a Songbird desde ahi ?

Es una buena forma de saber por donde pueden venir los problemas de incio de los programas.

S lo hiciste, mostra que mensajes te dio.

---

### Post by Fire_C10 on 2009-08-06
> **guillermolisi said:**
> Probaste de abrir una terminal/consola e invocar a Songbird desde ahi ?

Es una buena forma de saber por donde pueden venir los problemas de incio de los programas.

S lo hiciste, mostra que mensajes te dio.

Hammm lo trate de lanzar escribiendo su nombre (no se si se tine que hacer asi).

christian@christian-desktop:~$ songbird
Segmentation fault
christian@christian-desktop:~$ 


Reinstale ubuntu y me corrio, pero actualice ubuntu despues de instalarlo y ya no me volvio a correr.

---

### Post by guillermolisi on 2009-08-06
En los comentarios que han dejado en GetDeb, ver ultimo mensaje de NickCis, hay quienes les ha dado el mismo error (segmentation fault) y desisntalando libvisual-0.4-plugins les ha funcionado.

Otros han bajado la version no estable, desde un repositorio ppa donde se hacen modificaciones diariamente, y dicen que tambien les ha funcionado.

Como ya experimentaste, reinstalar no solo no te soluciona problemas como este sino que ademas no te permite aprender al no encontrar la verdadera causa.

Despues de la actualizacion, la libreria libvisual-0.4-plugins sigue desinstalada o se volvio a instalar ?

---

### Post by Fire_C10 on 2009-08-07
Tuve que reinstalar porque se murio mi disco duro y solo se oía el tipoco "Tack tack tack".

Sobre el libvisual-0.4-plugins lo tengo desistalado, y te digo que el problema me aparecio despues de la primera actualizacion que hice con ubuntu. Yo creo que me instalo la versión inestable y modificada que mencionas pero como?.

Saludos y gracias por sus respuestas!.

---

### Post by guillermolisi on 2009-08-07
La version que esta en los repositorios de Ubuntu es estable, puede no ser la ultima pero no es la de desarrollo/alpha/beta/rc/unstable.

La que mencione antes solo esta disponible en repositorios ppa que no juegan en la actualizacion de Ubuntu, salvo que los hayas incluido (manualmente en la lista de repositorios).

Probaste de remover completamente SongBird y volverlo a instalar despues de actualizar completamente Ubuntu ?

---

### Post by Fire_C10 on 2009-08-07
Actualice, pero no lo removí antes de actualizar, sobre el reposito ppa no tengo idea de como instalarlo.

---

### Post by Fire_C10 on 2009-08-07
Segun investigue es debido a un bug en globalmenu para gnome que causa que no pueda ser lanzado songbird en ubuntu x64.
[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=441](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=441)

---

### Post by guillermolisi on 2009-08-07
Y vos estas usando Ubuntu x64 ?

No recuerdo haber leido algo al respecto de tu parte, con lo que asumi que era i386.

Igual, si abris una consola/terminal y ejecutas songbird, lo de globalmenu no creo que juegue salvo que tambien lo tengas instalado (y que tampoco recuerdo haber leido sobre eso).

---

### Post by matias_tati on 2009-08-08
Yo la baje de aca y no desinstale ninguna librería ni nada quizás te sirva. Saludos!!!!
[http://www.getdeb.net/download/4460/0](http://www.getdeb.net/download/4460/0)

---

### Post by Fire_C10 on 2009-08-08
Bueno lo de ubuntu de 64bits se me paso mencionarlo jeje, pero lo de global menu no lo mencione porque a cada rato se instalan programas y no lo considere necesario, aunque si lo fué.

---

