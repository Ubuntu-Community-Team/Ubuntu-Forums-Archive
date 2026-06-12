---
title: "Amarok K9copy problema en gnome"
date: 2009-06-30
forum: Software
---

### Post by aledruetta on 2009-06-30
Hola Comunidad!

Estoy con un problema en dos aplicaciones "K": Amarok y K9copy.  No tengo certeza de que el problema sea común a las dos, pero son los problemas comenzaron al mismo tiempo, entonces, quizá estén relacionados.

Ubuntu Jaunty Jackalope. Gnome. Acer Aspire 4310.

Amarok: no reproduce los audios de la biblioteca. Esos audios están en un disco USB externo. Amarok los carga, organiza la biblioteca, pero no los reproduce (que sería lo más interesante en este caso ¿no?)

K9copy: cuando intento ingresar a la aplicación aparece un mensaje de error:
[html]Ha ocurrido un error fatal
 The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at http://bugs.kde.org. Useful details include how to reproduce the error, documents that were loaded, etc.
[/html]Esto comenzó a suceder (k9copy) mientras estaba intentando configurar la aplicación. Añadí el dispositivo cdrom0 y cuando di "aceptar" saltó la ventanita.

¿Alguna recomendación?
¿Cómo puedo brindar más información útil?

Saludos y muchas gracias,
Alejandro.

El mismo post en Chile Loco Team:
[http://ubuntuforums.org/showthread.php?p=7540216#post7540216](http://ubuntuforums.org/showthread.php?p=7540216#post7540216)

---

### Post by guillermolisi on 2009-06-30
> **aledruetta said:**
> Hola Comunidad!

Estoy con un problema en dos aplicaciones "K": Amarok y K9copy.  No tengo certeza de que el problema sea común a las dos, pero son los problemas comenzaron al mismo tiempo, entonces, quizá estén relacionados.

Ubuntu Jaunty Jackalope. Gnome. Acer Aspire 4310.

Amarok: no reproduce los audios de la biblioteca. Esos audios están en un disco USB externo. Amarok los carga, organiza la biblioteca, pero no los reproduce (que sería lo más interesante en este caso ¿no?)

K9copy: cuando intento ingresar a la aplicación aparece un mensaje de error:
[html]Ha ocurrido un error fatal
 The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at http://bugs.kde.org. Useful details include how to reproduce the error, documents that were loaded, etc.
[/html]Esto comenzó a suceder (k9copy) mientras estaba intentando configurar la aplicación. Añadí el dispositivo cdrom0 y cuando di "aceptar" saltó la ventanita.

¿Alguna recomendación?
¿Cómo puedo brindar más información útil?

Saludos y muchas gracias,
Alejandro.

El mismo post en Chile Loco Team:
[http://ubuntuforums.org/showthread.php?p=7540216#post7540216](http://ubuntuforums.org/showthread.php?p=7540216#post7540216)
Que version de Amarok estas usando ?
Los audios, en que formato estan ?

Sobre K9Copy, lo que haria es invocarlo desde una terminal/consola para ver si brinda mas informacion.

---

### Post by aledruetta on 2009-06-30
> **guillermolisi said:**
> Que version de Amarok estas usando ?
Los audios, en que formato estan ?

Sobre K9Copy, lo que haria es invocarlo desde una terminal/consola para ver si brinda mas informacion.

Amarok 2.0.2
Formato de audio: mp3
Tamaño de la biblioteca: 60 Gb.
Consola:
```
alejandro@alejandro-laptop:~$ k9copy
KCrash: Application 'k9copy' crashing...
sock_file=/home/alejandro/.kde/socket-alejandro-laptop/kdeinit4__0
```Además de dar ese mensaje, la consola abre la misma ventana de error que ya mencioné.

Gracias Guillermo.

Respuestas en el otro post: 
[http://ubuntuforums.org/showthread.php?p=7540323#post7540323](http://ubuntuforums.org/showthread.php?p=7540323#post7540323)

---

### Post by guillermolisi on 2009-06-30
> **aledruetta said:**
> Amarok 2.0.2
Formato de audio: mp3
Tamaño de la biblioteca: 60 Gb.
Consola:
```
alejandro@alejandro-laptop:~$ k9copy
KCrash: Application 'k9copy' crashing...
sock_file=/home/alejandro/.kde/socket-alejandro-laptop/kdeinit4__0
```Además de dar ese mensaje, la consola abre la misma ventana de error que ya mencioné.

Gracias Guillermo.

Respuestas en el otro post: 
[http://ubuntuforums.org/showthread.php?p=7540323#post7540323](http://ubuntuforums.org/showthread.php?p=7540323#post7540323)

Mira, me da la impresion de que algo puede no estar bien con versiones de librerias KDE 4 para que ambas aplicaciones funcionen bien (conteste algo parecido en el thread del foro chileno).

Cuando le das Play a Amarok sobre un archivo mp3, comienza su reproduccion pero no se escucha nada (podes fijarte el indicador de avance de reproduccion que tiene Amarok en su parte superior) o sencillamente no hace nada de nada ?

Tenes conexion a Internet habilitada cuando haces esta comprobacion ?
Me ha pasado de que no funciono Amarok al reproducir mp3 porque no podia resolver la tapa del disco que queria escuchar por tener Internet caida.

Podes reproducir mp3 con otro reproductor del entorno Gnome ?

---

### Post by aledruetta on 2009-06-30
> **guillermolisi said:**
> Mira, me da la impresion de que algo puede no estar bien con versiones de librerias KDE 4 para que ambas aplicaciones funcionen bien (conteste algo parecido en el thread del foro chileno).

En ese caso ¿qué podría hacer?

> **guillermolisi said:**
> Cuando le das Play a Amarok sobre un archivo mp3, comienza su reproduccion pero no se escucha nada (podes fijarte el indicador de avance de reproduccion que tiene Amarok en su parte superior) o sencillamente no hace nada de nada ?

Aparentemente, comienza la ejecución, porque a partir de ahí, en el menú contextual únicamente me habilita pause y stop. Pero no aparece el indicador de avance de reproducción. Digamos, aparece, pero no avanza.

> **guillermolisi said:**
> Tenes conexion a Internet habilitada cuando haces esta comprobacion ?
Me ha pasado de que no funciono Amarok al reproducir mp3 porque no podia resolver la tapa del disco que queria escuchar por tener Internet caida.

Tengo conexión a Internet, sí.

> **guillermolisi said:**
> Podes reproducir mp3 con otro reproductor del entorno Gnome ?

Rhythmbox reproduce.

Otra pregunta, Guillermo, vos que sos usuario de KDE y Amarok, ¿leíste en el otro foro lo que pasó con mi biblioteca? ¿a qué se debió eso? Si Amarok fuese una cosa física ya lo hubiese destrozado a martillazos. 

Saludos,
Alejandro.

---

### Post by guillermolisi on 2009-06-30
Por el tema de las versiones de librerias habria que verificar una por una para saber que las versiones de las instaldas se corresponden con las que necesita Amarok 2.0.2

Otra alternativa es actualizar a 2.1.1, la ultima estable, asi te deberia resolver otra vez sus dependencias y actualizar auqellas que no esten adecuadas en sus versiones. Esta version es la que estoy usando actualmente y funciona notablemente mejor que sus antecesoras de version 2 (la version anterior a la 2.0 era increiblemente estable y funcional y tambien se puede usar en JJ.)

Respecto del desorden que te produjo en tu pendrive, no se que decirte porque nunca deje que administre contenidos. Siempre lo hice a mano (un directorio del interprete/autor y dentro directorios por album/CD).

Tenes alguna otra aplicacion multimedia para KDE en uso ?

---

### Post by aledruetta on 2009-06-30
> **guillermolisi said:**
> Por el tema de las versiones de librerias habria que verificar una por una para saber que las versiones de las instaldas se corresponden con las que necesita Amarok 2.0.2

No, prefiero seguir usando Rhythmbox, que no me gusta, pero no me complica tanto la vida. 

> **guillermolisi said:**
> Otra alternativa es actualizar a 2.1.1, la ultima estable, asi te deberia resolver otra vez sus dependencias y actualizar auqellas que no esten adecuadas en sus versiones. Esta version es la que estoy usando actualmente y funciona notablemente mejor que sus antecesoras de version 2 (la version anterior a la 2.0 era increiblemente estable y funcional y tambien se puede usar en JJ.)

Esto voy a intentarlo, a ver qué resultado da.

> **guillermolisi said:**
> Respecto del desorden que te produjo en tu pendrive, no se que decirte porque nunca deje que administre contenidos. Siempre lo hice a mano (un directorio del interprete/autor y dentro directorios por album/CD).

Yo tenía organizada mi música por Continentes, Países, Autores y Albums. Ahora desaparecieron las carpetas originales y quedaron carpetas por autor que adentro tienen sus albums. Pero como se ve que Amarok se guió por los tags, y los tags no estaban completos para todas las carpetas, ahora por ejemplo tengo un autor que "Track 1" con temas mezclados de distintos discos. Maldición!!!

> **guillermolisi said:**
> Tenes alguna otra aplicacion multimedia para KDE en uso ?

Tengo Songbird, Rhythmbox, VLC, Totem, Amarok y Kino. ¿Kino es KDE?


Gracias nuevamente,
Alejandro.

---

### Post by staar on 2009-06-30
amarok te reorganizó la colección? por lo que sé, puede hacer eso, pero solo bajo demanda del usuario, nunca solo, y es un proceso lento, con varios diálogos de confirmación antes de que empieze...

mirá, te recomendaría lo básico, desinstalarlo completamente y volverlo a instalar desde cero, y sino funciona, y no te gusta rhythmbox, podés probar otros reproductores en GTK más similares a amarok, como exaile, banshee o gmusicbrowser...

saludos

---

### Post by aledruetta on 2009-07-01
> **staar said:**
> amarok te reorganizó la colección? por lo que sé, puede hacer eso, pero solo bajo demanda del usuario, nunca solo, y es un proceso lento, con varios diálogos de confirmación antes de que empieze...

La verdad que no sé cómo fue que reorganizó la biblioteca. Seguramente yo apreté algún botón, ahora, que yo recuerde no hubo dialogos de aviso porque supongo que me hubiese dado cuenta. Pero bueh, todo es posible...

> **staar said:**
> mirá, te recomendaría lo básico, desinstalarlo completamente y volverlo a instalar desde cero, y sino funciona, y no te gusta rhythmbox, podés probar otros reproductores en GTK más similares a amarok, como exaile, banshee o gmusicbrowser...

Ya probé desinstalar e instalar nuevamente; y probé también instalar la última versión estable de la página de Amarok. Sigue sin funcionar.

Saludos y gracias,
Alejandro.

---

### Post by aledruetta on 2009-07-01
La solución al problema de K9copy, aquí:
[http://ubuntuforums.org/showthread.php?p=7546018#post7546018](http://ubuntuforums.org/showthread.php?p=7546018#post7546018)

---

