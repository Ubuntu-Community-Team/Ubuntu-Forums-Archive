---
title: "Reiniciar Gnome sin reinicar el PC."
date: 2009-06-24
forum: Software
---

### Post by ParamDaya on 2009-06-24
[FONT=Georgia][SIZE=2][B]Estimados

La investigacion que he hecho al respecto me arrojo lo siguiente:

Usar CTRL+ALT+BACKSPACE: En mi PC no funciono, o sea, no hizo nada.

O sudo /etc/init.d/gdm restart  : En mi PC lo reinicio por completo.

La duda viene dada porque he instalado y aprendido a instalar temas para Ubuntu y temas para el mouse tambien, ahora bien, cuando instalas ciertos temas, y sobre todo los temas de mouse, estos no se ejecutan por completo hasta que reinicies el PC.

Entonces pense en buscar alguna forma de reiniciar el escritorio o Gnome para que tomara efecto todas las caracteristicas de los temas.

Pero no he encontrado nada, salvo lo mas arriba mencionado que termina por reiniciar todo el PC.

Alguien tiene alguna idea?

Muchas gracias.[/B][/SIZE][/FONT]

---

### Post by moreback on 2009-06-24
Simple: cierra tu sesión y logueate de nuevo.

---

### Post by Carlos C on 2009-06-24
Existe una forma de habilitar el atajo de teclas control+alt+bacspace que ha sido deshabilitado en Jaunty (asumo que es Jaunty la versión con la que estás trabajando, por favor recuerda decir este detalle siempre que consultes en el foro). Una manera simple es instalar y hablitar dontzap:
```
sudo apt-get install dontzap
sudo dontzap -d
```Otra manera es editar tu archivo xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```Añades la siguiente sección:
```
Section "ServerFlags"
    Option    "DontZap"    "no"
EndSection
```

---

### Post by kamus on 2009-06-24
> **ParamDaya said:**
> [FONT=Georgia][SIZE=2][B]Estimados

La investigacion que he hecho al respecto me arrojo lo siguiente:

Usar CTRL+ALT+BACKSPACE: En mi PC no funciono, o sea, no hizo nada.

O sudo /etc/init.d/gdm restart  : En mi PC lo reinicio por completo.

La duda viene dada porque he instalado y aprendido a instalar temas para Ubuntu y temas para el mouse tambien, ahora bien, cuando instalas ciertos temas, y sobre todo los temas de mouse, estos no se ejecutan por completo hasta que reinicies el PC.

Entonces pense en buscar alguna forma de reiniciar el escritorio o Gnome para que tomara efecto todas las caracteristicas de los temas.

Pero no he encontrado nada, salvo lo mas arriba mencionado que termina por reiniciar todo el PC.

Alguien tiene alguna idea?

Muchas gracias.[/B][/SIZE][/FONT]

```

sudo /etc/init.d/gdm restart

```

Deberia ser suficiente..

Viste los logs de xorg y xsession-errors?

Saludos

---

### Post by Patriciologico on 2009-06-27
ParamDaya, la idea de usar negritas es **resaltar** o **dar enfasis** en ciertas palabras, ideas, frases. Pero si lo usas en todo tu post, **resulta molesto para la vista** . Yo me acerco con todo el animo a tratar de ayudarte, pero cuando veo todo en negrita me desanimo. Espero tomes el consejo.

Saludos!

---

