---
title: "Minimizar, Maximizar y cerrar &quot;cambiados&quot;"
date: 2010-03-07
forum: Software
---

### Post by atari130xe on 2010-03-07
Gente, me pasó algo "raro" las opciones de mis ventanas "Minimizar, Maximizar y Cerrar" están "cambiadas" de lugar, eso hace que se minimizen ventanas cuando en realidad las quiero maximizar, alguien sabe a que se debe y como corregirlo?
Gracias! :p

Va el "pantallazo" con el puntero marcando el incoveniente:

[IMG]http://img704.imageshack.us/img704/2506/pantalla1.png[/IMG]

---

### Post by lega on 2010-03-07
estuviste jugando con los nuevos themes de Ubuntu? digo porque vienen con los botones cambiados.

Se soluciona tipeando alt+f2 dentro de la caja de dialogo tipear gconf-editor, en el menu que se abre vas a apps->metacity->general-> sobre el cuadro de diálogo de la derecha busca el apartado "button_layout" y cambialo por esto "menu:minimize,maximize,close" sin las comillas.

Espero te sirva

---

### Post by atari130xe on 2010-03-07
> **lega said:**
> estuviste jugando con los nuevos themes de Ubuntu? digo porque vienen con los botones cambiados.

Se soluciona tipeando alt+f2 dentro de la caja de dialogo tipear gconf-editor, en el menu que se abre vas a apps->metacity->general-> sobre el cuadro de diálogo de la derecha busca el apartado "button_layout" y cambialo por esto "menu:minimize,maximize,close" sin las comillas.

Espero te sirva

Asi es... los nuevos themes de Lucid, gracias!

---

