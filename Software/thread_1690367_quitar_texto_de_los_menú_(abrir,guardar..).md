---
title: "quitar texto de los menú (abrir,guardar..)"
date: 2011-02-18
forum: Software
---

### Post by 3nG3ndR0 on 2011-02-18
hola como dice el titulo quiero quitar el texto del que aparece en algunos menú como muestro en la imagen

[IMG]http://img6.imagebanana.com/img/fq139rkn/Seleccin_001.png[/IMG]

quiero solo dejar los iconos

---

### Post by juboba on 2011-02-18
¿qué menú es ese?

---

### Post by 3nG3ndR0 on 2011-02-18
gedit, filer roller etc...

---

### Post by Carlos C on 2011-02-19
Hola.
Tienes que abrir el gconf-editor (sé que tú lo sabes, pero para los que no sepan: presionando las teclas ALT+F2 aparece una ventana donde escriben gconf-edfitor). Debes entrar en  *desktop>gnome>interface* y cambias el valor del campo *toolbar_style.* Por defecto su valor es "both-horiz", debes cambiarlo por "icons". Con eso quedará como tú quieres.******

---

### Post by 3nG3ndR0 on 2011-02-21
> **Carlos C said:**
> Hola.
Tienes que abrir el gconf-editor (sé que tú lo sabes, pero para los que no sepan: presionando las teclas ALT+F2 aparece una ventana donde escriben gconf-edfitor). Debes entrar en  *desktop>gnome>interface* y cambias el valor del campo *toolbar_style.* Por defecto su valor es "both-horiz", debes cambiarlo por "icons". Con eso quedará como tú quieres.******


wooo genial es justo lo que buscaba, me funciono gracias

---

