---
title: "borre los iconos del escritorio y naultilus no abre"
date: 2008-07-30
forum: Software
---

### Post by kornykyano on 2008-07-30
Hace un momento toque algo que no debia tocar
Fui al editor de configuraciones y entre a /apps/nautilus/desktop/computer_icon_name , inicialmente decia <sin valor> y lo cambie a 1 (no me pregunten que quice hacer!)
resulta que ahora no puedo ingresar a nautilus, desde terminal me dice:

> Initializing nautilus-share extension
seahorse nautilus module initialized
**
** Eel:ERROR:(eel-preferences.c:116):preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Cancelado

Y al iniciar sesion me aparece el siguiente mensaje:

> Ha ocurrido un error mientras cargaba o guardaba la información de la configuración para gnome-panel. Puede que algunas de las opciones de configuración no funcionen.

Tipos incompatibles: Esperaba «string» y se obtuvo «int» para la clave /apps/nautilus/desktop/computer_icon_name

por favor alguien me puede ayudar!

saludos

dejo una imagen
[http://i37.tinypic.com/jrffwi.png]("http://i37.tinypic.com/jrffwi.png")

---

### Post by pol666 on 2008-07-30
Y no lo volviste a cambiar?

hace alt+F2 y ahi pone gconf-editor, volve a donde estaba lo que tocaste y ponele 0 de vuelta.

---

### Post by kornykyano on 2008-07-30
> **pol666 said:**
> Y no lo volviste a cambiar?

hace alt+F2 y ahi pone gconf-editor, volve a donde estaba lo que tocaste y ponele 0 de vuelta.

si... ya lo cambie a 0 pero sigue dando el mismo error

---

### Post by Hei Ku on 2008-07-30
cambialo a <sin_valor>, o sea borra esa entrada directamente.

---

### Post by kornykyano on 2008-07-30
> **Hei Ku said:**
> cambialo a <sin_valor>, o sea borra esa entrada directamente.

solucionado!!! eliminando esa entrada y reiniciando el sistema vuelve todo a la normalidad. :)

debo tener mas cuidado. debo tener mas cuidado. debo tener mas...

Gracias Hei Ku y pol666

---

### Post by User21 on 2008-08-01
Por favor, marcar el hilo como** [SOLVED]** . Saludos!

---

