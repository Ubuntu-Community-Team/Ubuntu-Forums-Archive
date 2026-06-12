---
title: "Problema con JPEG's"
date: 2009-01-25
forum: Software
---

### Post by AlucardArg on 2009-01-25
Hola gente!
Hace tiempo estoy dando vuelta por los foros de Ubuntu, pero esta es la 1ra vez que posteo...

En fin, tengo un pequeño gran problema:
Hace pocos dias hice el cambio a Ubuntu. Ya un par de veces habia cambiado, pero siempre volvia por una, u otra razon, pero ahora mepa que ya quedo aca.
La cuestion es que anoche estuve toqueteando mil cosas, personalizando y cambiando cosas. Uno de esos cambios, fue instalar Conky (previamente ya instalé GTK+ 2.0, y otras cosas, pero me parece que el problema surgio despues de un reinicio).
Hoy a la tarde apago la PC, y recien vengo, enciendo, y veo que no tengo fondo de escritorio, y que no puedo abrir JPEGs con el Image Viewer, ni con F-Spot (pero si con GIMP y Firefox)! Asimismo, si entro en la carpeta de Imagenes, los thumbnails se ven bien, sea cual sea el formato.

Alguien tiene idea de que podrá ser?

Estoy corriendo Ubuntu Ibex, kernel 2.6.27-9-generic


EDIT: Ahora noto que, en la lista de los themes, solo aparecen los que bajé de inet, y si no me equivoco, son todos de GTK+ 2.0. Y ademas, que si cambio el cursor, solo aparece "cambiado" cuando esta sobre el escritorio, o sobre la barra de tareas/menues, no sobre el firefox.

No tengo ganas de reinstalar todo ubuntu desde cero, despues de tanto quilombo! D:<


EDIT2: Hace un rato, solo, se salio todo el theme, y quedo parecido a Windows 98! Iconos genericos (tipo una hoja de papel), y todo gris... Reinicie y me volvio a tomar los themes, pero parece un virus todo esto!
Estaba escribiendo "parece un virus" y justamente paso de nuevo... LA **** MADREEEEEEEEEE

---

### Post by guillermolisi on 2009-01-25
> **AlucardArg said:**
> Hola gente!
Hace tiempo estoy dando vuelta por los foros de Ubuntu, pero esta es la 1ra vez que posteo...

En fin, tengo un pequeño gran problema:
Hace pocos dias hice el cambio a Ubuntu. Ya un par de veces habia cambiado, pero siempre volvia por una, u otra razon, pero ahora mepa que ya quedo aca.
La cuestion es que anoche estuve toqueteando mil cosas, personalizando y cambiando cosas. Uno de esos cambios, fue instalar Conky (previamente ya instalé GTK+ 2.0, y otras cosas, pero me parece que el problema surgio despues de un reinicio).
Hoy a la tarde apago la PC, y recien vengo, enciendo, y veo que no tengo fondo de escritorio, y que no puedo abrir JPEGs con el Image Viewer, ni con F-Spot (pero si con GIMP y Firefox)! Asimismo, si entro en la carpeta de Imagenes, los thumbnails se ven bien, sea cual sea el formato.

Alguien tiene idea de que podrá ser?

Estoy corriendo Ubuntu Ibex, kernel 2.6.27-9-generic


EDIT: Ahora noto que, en la lista de los themes, solo aparecen los que bajé de inet, y si no me equivoco, son todos de GTK+ 2.0. Y ademas, que si cambio el cursor, solo aparece "cambiado" cuando esta sobre el escritorio, o sobre la barra de tareas/menues, no sobre el firefox.

No tengo ganas de reinstalar todo ubuntu desde cero, despues de tanto quilombo! D:<


EDIT2: Hace un rato, solo, se salio todo el theme, y quedo parecido a Windows 98! Iconos genericos (tipo una hoja de papel), y todo gris... Reinicie y me volvio a tomar los themes, pero parece un virus todo esto!
Estaba escribiendo "parece un virus" y justamente paso de nuevo... LA **** MADREEEEEEEEEE

De donde bajaste GTK+2.0 ? Como lo instalaste ?

Esa pantalla horrible que ves es la interfaces X pelada, sin la capa del Gnome arriba.

Me da la impresion que por algun motivo Gnome (GDM) se esta cayendo y por eso solo ves la interface X en bruto.

Te fijaste en los logs ? (/var/log) Por ejemplo en dmesg, messages. O en /var/log/gdm/:0.log ?

---

### Post by AlucardArg on 2009-01-26
El GTK lo habia bajado de Linux From Scratch.
Y si, se caia a pedazos el sistema... Ya tenia varios errores mas, y opte por reinstalar Ubuntu de cero.
Y si, revise los logs, y creo que no decia nada fuera de lo comun sobre X, ni nada...
Leccion: No jodan con GTK y sus dependencias, si no saben bien que hacen -___-

Igual, gracias guille por la respuesta!

---

