---
title: "Fonts en negrita en el panel"
date: 2009-11-16
forum: Software
---

### Post by Tosh78 on 2009-11-16
Hola! Bueno, resulta que en el panel de Gnome las fonts que estan activadas estan como "negrita" o "bold" en ingles. 
Alguien sabe donde puedo sacarle la opcion de negrita a esa tipografia?
Lo loco es que me aparecio solamente a partir de que instale karmic, ya que antes tenia lo mismo y no estaba en negrita.
No es algo que me haga dejar de funcionar el sistema, pero esteticamente no me convence.

---

### Post by josecuervo86 on 2009-11-16
No tendras activado el "suavisado de subpixel" no? Eso se pone en la sección tipografía y le da como un mayor ancho a las fuentes, pero no se si necesariamente al punto de ser negrita

---

### Post by Sleeping Beauty on 2009-11-16
Yo le dí mil vueltas por lo mismo, pero por todo lo que anduve probando sólo es con el tema Dust.

---

### Post by Tosh78 on 2009-11-17
Hola!
Josecuervo, si tengo seleccionada esa opcion, pero sin embargo a lo que me refiero es a que la letra realmente esta Bold.
Sleepingbeauty, es cierto, es solo con el tema Dust. Probe cambiar a otros temas y aparece la letra normal.
Alguien sabe como cambiar esto segun el tema? Alguna sugerencia?

---

### Post by pablo.s on 2009-11-17
> **Tosh78 said:**
> Alguien sabe como cambiar esto segun el tema? Alguna sugerencia?

Dentro del archivo /usr/share/themes/Dust/gtk-2.0/gtkrc
hay una parte en la que está esto:

```
# The following lines make panel-menu-applet, slab-main-menu and gimmie applet's text bold. The radius value sets the roundness value of the selected menu-item.
style "bold-panel-menu"
{
    font_name = "Bold"

    engine "murrine" {
    roundness = 2
    }
}

style "bold-panel-slab"
{
    font_name = "Bold"
}
widget "*Panel*slab-main-menu-panel-button*" style "bold-panel-slab"
widget "*gimmie*" style "bold-panel-slab"
widget "*Panel*MenuBar*" style "bold-panel-menu"
widget "*Panel*Clock*" style "bold-panel-menu"

widget "gtk-tooltip*" style "tooltips"

```

Cambiale la parte que dice "Bold" por otra fuente.

---

### Post by Tosh78 on 2009-11-18
Muchas gracias Pablo! Comente esas lineas y ahora no esta bold. Mucho mas lindo :)

---

### Post by guillermolisi on 2009-11-18
> **Tosh78 said:**
> Muchas gracias Pablo! Comente esas lineas y ahora no esta bold. Mucho mas lindo :)
Then, is it solved ?

---

### Post by Sleeping Beauty on 2009-11-18
Gracias Pablo por acá también, la verdad es que había desistido de usar el tema porque no sabía como cambiar la tipografía :D

---

### Post by pablo.s on 2009-11-18
> **Sleeping Beauty said:**
> Gracias Pablo por acá también, la verdad es que había desistido de usar el tema porque no sabía como cambiar la tipografía :D

> **Tosh78 said:**
> Muchas gracias Pablo! Comente esas lineas y ahora no esta bold. Mucho mas lindo :)

Gracias a ustedes por usar GNOME!

PD: Me salió el fan de adentro y bueno...

---

