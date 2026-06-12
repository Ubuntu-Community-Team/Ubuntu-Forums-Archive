---
title: "no funciona &quot;ã&quot; (a con tilde portugués) en 8.10"
date: 2008-11-07
forum: Software
---

### Post by Irishpolyglot on 2008-11-07
Hola a todos!! :)
Actualicé mi distro a 8.10 hace poco y casi todo funciona muy bien. Pero el teclado no funciona como antes. En 8.04 la combinación [ALT GR] + 4 y luego "a" o "o" dio ã o õ, y ya sólo da ~a o ~o. Es que escribo en portugués también. Sé que es muy fácil cambiar entre el teclado portugués y español (ahora pulso ALT + tecla de mayúsculas y cambia) pero en 8.10 todo funcionaba en el teclado español.
La configuración original sigue con el teclado español (de España) y ñ, ó, ï, ô etc. funcionan.
¿Hay algo que puedo hacer? :)
Gracias!

---

### Post by c4d0rn4 on 2008-11-08
> **Irishpolyglot said:**
> Hola a todos!! :)
Actualicé mi distro a 8.10 hace poco y casi todo funciona muy bien. Pero el teclado no funciona como antes. En 8.04 la combinación [ALT GR] + 4 y luego "a" o "o" dio ã o õ, y ya sólo da ~a o ~o. Es que escribo en portugués también. Sé que es muy fácil cambiar entre el teclado portugués y español (ahora pulso ALT + tecla de mayúsculas y cambia) pero en 8.10 todo funcionaba en el teclado español.
La configuración original sigue con el teclado español (de España) y ñ, ó, ï, ô etc. funcionan.
¿Hay algo que puedo hacer? :)
Gracias!

Fijate si tenés de verdad un teclado español españa, [http://en.wikipedia.org/wiki/Keyboard_layout#Spanish_.28Spain.29](http://en.wikipedia.org/wiki/Keyboard_layout#Spanish_.28Spain.29) la mayoría que veo son el latinamericano. Por ahí poniendo bien la configuración de teclado apretando la tecla con el simbolo de ese acento y luego la letra agarre bien.

---

### Post by Irishpolyglot on 2008-11-08
Gracias por la respuesta! Por desgracia todavía no funciona...

Me aseguré de tener el teclado español *de España*en las configuraciones. Fue una buena idea controlarlo ya que veo que no hay esa opción en el teclado latinoamericano.

Lo intenté con la versión normal de España, la versión catalana de España, español latinoamericano etc. pero todavía me sale igual al intentar escribir ã (que sí que funciona si elijo teclado brasileño)... y tengo el teclado de España de tu enlace imprimido físicamente en el teclado, aunque eso no importa claro.

¿Funciona para vos, la ã con teclado español de España? O hay algo que hice mal al instalar 8.10 o cambiaron cómo funciona el teclado español de España en Intreprid, no sé...

---

### Post by c4d0rn4 on 2008-11-08
yo tengo el latinoamericano, toco alt GR+ la tecla que tiene ~ y luego la a y me marca ã.

no es la solución, pero probá con la configuración latina. alt gr+ la tecla que tiene * y +, y luego apretá la a.

con alt+f2 y luego ejecutas gucharmap vas a tener el mapa de caracteres. Hay un codigo para cada letra, pero no se como se introduce.

---

### Post by Irishpolyglot on 2008-11-08
> **c4d0rn4 said:**
> yo tengo el latinoamericano, toco alt GR+ la tecla que tiene ~ y luego la a y me marca ã.

no es la solución, pero probá con la configuración latina. alt gr+ la tecla que tiene * y +, y luego apretá la a.

con alt+f2 y luego ejecutas gucharmap vas a tener el mapa de caracteres. Hay un codigo para cada letra, pero no se como se introduce.

Gracias c4d0rn4 pero también con el teclado latinoamericano me sale el ~ al pulsar alt GR + esa tecla (en vez de esperar hasta que entre la próxima letra)... ¿hay una manera para directamente codificar símbolos y letras especiales por una combinación de teclas? Si no, uso ALT + tecla de mayúsculas para cambiar al teclado portugués si quiero aceder la ã... muy raro que no funcione :(

---

### Post by pol666 on 2008-11-08
Off topic:

Estuve "chusmeando" un poco  tu vida, y es de lo mas interesante, Suerte en tus viajes :D


Saludos

---

### Post by Irishpolyglot on 2008-11-08
> **pol666 said:**
> Off topic:

Estuve "chusmeando" un poco  tu vida, y es de lo mas interesante, Suerte en tus viajes :D


Saludos

jajaja muchísimos gracias pol666!! Muy amable :) Todavía me quedo un mes acá en BsAs - me encanta la ciudad!! Si te gusta mi blog, no olvides subscribir por RSS! Voy a enviar un video sobre mi experiencia de aprender el tango :D

Luego me esperan en India claro!! :p

Bueno, así perdí la ã por sólo dos teclas para siempre? :confused:

---

### Post by sergiom99 on 2008-11-08
hola, yo en KDE puse este codigo en el archivo /etc/X11/xorg.conf, en la parte del teclado y me sirve para usar la tecla Windows Izquierda como "tecla compose"
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection
 
```
entonces apreto LWin+'+a y tengo á, o LWIN+-+n = ñ

espero te sirva.

---

### Post by Arash_h on 2010-01-30
> **c4d0rn4 said:**
> yo tengo el latinoamericano, toco alt GR+ la tecla que tiene ~ y luego la a y me marca ã.

no es la solución, pero probá con la configuración latina. alt gr+ la tecla que tiene * y +, y luego apretá la a.

con alt+f2 y luego ejecutas gucharmap vas a tener el mapa de caracteres. Hay un codigo para cada letra, pero no se como se introduce.

Hola, amigo,
Me pasaba lo mismo, pero al intentar de la manera siguiente lo arregle:
CTRL + ALT JUNTO A TECLA "+", Y LUEGO LA VOCAL RESPECTIVA.

Saludos

---

### Post by patocardo on 2010-03-19
> **Arash_h said:**
> Hola, amigo,
Me pasaba lo mismo, pero al intentar de la manera siguiente lo arregle:
CTRL + ALT JUNTO A TECLA "+", Y LUEGO LA VOCAL RESPECTIVA.

Saludos

Quería aclarar que no es lo mismo &#257; (que es lo que sale con esa combinación de teclas) que ã , que es lo que estamos buscando
Estoy detrás de este asunto hace varios días y no consigo "dar en la tecla". Lo ideal sería una aplicación para asignar caracteres a las combinaciones de teclas, pero por lo menos estaría bueno saber en código cómo se cambia. Yo tengo Ubuntu 9.10 y no me responde a nada cuando designo la "Compose Key".
Por lo pronto me instalé Autokey, y añadí una frase que era la letra en cuestión, con la abreviación de ~ seguido por a, pero el día que quiera poner los dos caracteres juntos, tendré que desactivar el programa, escribirlos y activarlo de vuelta, muy engorroso

---

### Post by daphyre on 2013-01-03
Este es un problema recurrente y sin solución sencilla en Internet, pero he encontrado que es mucho más simple de lo que todos intentan. Solo hay que ir a **opciones de Teclado**, y cambiar el teclado (Español/Latinoamericano) normal, por el que dice **"Teclado con tilde muerta"**. De esta forma, permite usar **~** con **ã**, **õ**, **ñ**, etc, y para insertar la tilde, solo se debe presionar dos veces el símbolo ~.

Esta opción también viene para ser elegida cuando se instala Ubuntu por primera vez en una PC. Espero esto sirva también a gente que busque la solución en un futuro como lo hice yo hoy :)

---

### Post by HernanLinux93 on 2013-01-04
> **daphyre said:**
> Este es un problema recurrente y sin solución sencilla en Internet, pero he encontrado que es mucho más simple de lo que todos intentan. Solo hay que ir a **opciones de Teclado**, y cambiar el teclado (Español/Latinoamericano) normal, por el que dice **"Teclado con tilde muerta"**. De esta forma, permite usar **~** con **ã**, **õ**, **ñ**, etc, y para insertar la tilde, solo se debe presionar dos veces el símbolo ~.
 
Esta opción también viene para ser elegida cuando se instala Ubuntu por primera vez en una PC. Espero esto sirva también a gente que busque la solución en un futuro como lo hice yo hoy :)
 
 
genial es lo intente y funciono, gracias por la explicacion ;)

---

