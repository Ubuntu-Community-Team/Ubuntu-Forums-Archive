---
title: "Paneles en Ubuntu desordenados"
date: 2009-06-09
forum: Software
---

### Post by Rago on 2009-06-09
Hola, otra vez yo.

Tengo ubuntu Hardy. El panel de "inicio" de ubuntu la ubique abajo al igual que otro panel para desplegar las ventanas abiertas. El problema es que al reiniciar estos paneles se desordenan, es decir, se cambian de posicion al igual que los iconos. No es para nada grabe pero si molesto(tengo compiz).

Alguna idea de como solucionarlo?

De antemano gracias.

---

### Post by Patriciologico on 2009-06-09
Abre el editor de configuracion:

```
gconf-editor
```

Dentro de las opciones "Apps" luego &#8220;Panel&#8221;, selecciona &#8220;Global&#8221; y activa la opción &#8220;locked down&#8221;

Otra forma de hacerlo es intalando [UbuntuTweak]("http://ubuntu-tweak.com/screenshots") En la opcion Escritorio/Gnome/ activas bloquear paneles.

Ademas cada icono o applet agregado en el panel, pude ser bloqueado, haciendo click derecho y activando la opcion.

Raro el problema, me gustaria saber por que se da.

Saludos!

---

### Post by Carlos C on 2009-06-09
A mí se me desordena cuando extiendo el escritorio o cosas por el estilo que tengan que ver con modificar el tamaño del escritorio.

---

### Post by Rago on 2009-06-15
Hola otra vez.

Hice lo que me dijieron gconf-editor, pero sigue ocurriendo lo mismo, se los muestro con imagenes.

Asi tengo los paneles:

[[IMG]http://img134.imageshack.us/img134/5354/panel1.jpg[/IMG]]("http://img134.imageshack.us/i/panel1.jpg/")


Cuando reinicio, queda asi:

[[IMG]http://img230.imageshack.us/img230/1145/panel2.jpg[/IMG]]("http://img230.imageshack.us/i/panel2.jpg/")

Tengo bloqueados ambos paneles en la opcion que da al hacerles click derecho con el mouse.

Saludos.

---

### Post by Carlos C on 2009-06-15
¿No has pensado en juntar ambos paneles en uno?

---

### Post by moreback on 2009-06-16
No sé si funcionará (no lo puedo probar ya que uso un solo panel) pero ¿qué tal si cambias el orden de los paneles que aparece en la clave **/apps/panel/general/toplevel_id_list**?

Abre el **Editor de configuración** (gconf-editor) y navega hasta encontrar la clave anterior, luego hazle doble clic en el valor que aparece y usa los botones **Subir** y **Bajar** para invertir el orden. Después de esto reinicia tu sesión.

Saludos!

---

### Post by Rago on 2009-06-19
Hola.

Hice lo que me dijo moreback, reinicie pero ahora los paneles al hacerles click derecho me dan solo 2 opciones(ayuda, acerca de), entre a gconf-editor y ahora no me aparece nada en"/apps/panel/general/toplevel_id_list", parece que algo malo hice, pero solamente modifique lo que el amigo me dijo arriba.

Ojala me puedan ayudar.

---

### Post by Carlos C on 2009-06-19
¿y no es posible volver atrás?

---

### Post by moreback on 2009-06-19
mmh... ojalá te acordaras que nombres salían ahí para que los reescribieras.

Por lo visto se te borraron.

PD: Los nombres los puedes sacar de /apps/panel/toplevels

---

### Post by Rago on 2009-06-26
Hola a todos.
Sigo con el problema, de alguna manera extraña al reniciar el equipo estaban las lineas que se habian "borrado"(bottom_panel_screen0 y top_panel_screen0), pero el problema en los paneles persiste(solo me muestra las opciones ayuda, acerca de) y por lo visto la opcion "/apps/panel/general/toplevel_id_list" esta igual como estaba antes de modificarla.

¿Habra alguna opcion de desinstalar los paneles para instalarlos de 0?

Se agradecen sus respuestas.

---

### Post by Patriciologico on 2009-06-26
¿Has probado crearte un nuevo usuario?

---

### Post by Carlos C on 2009-06-26
También está la opción de eliminar ambos paneles y volverlos a crear. Luego añades los elementos que tenían los antiguos.

---

