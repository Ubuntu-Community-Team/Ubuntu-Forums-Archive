---
title: "¿Como edito la mini aplicación de indicadores en Lucid?"
date: 2010-10-29
forum: Software
---

### Post by atari130xe on 2010-10-29
Gente, instalé para ver que onda el escritorio Unity y el resultado fué:
1) no funcionó (me quedó una mezcla de Gnome con Unity)
2) también quedó un "hermoso" "file Editar Desktop" menú extra en la miniaplicación de indicadores.
¿Alguien sabe como eliminar ese menú de la miniaplicación de indicadores? ya intenté un par de cosas pero no encuentro como sacar ese menú que además agregó la hora por partida doble.
Gracias!

Les dejo una imagen con el puntero sobre el menú en cuestión:

[[IMG]http://img827.imageshack.us/img827/5428/pantallazo2h.png[/IMG]](http://img827.imageshack.us/i/pantallazo2h.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by hectorivand on 2010-10-29
Lo que podes hacer es restaurar los paneles por defecto de gnome.

```
gconftool-2 –recursive-unset /apps/panel
```Eso va a servir.

Saludos
Nacho

---

### Post by atari130xe on 2010-10-29
> **hectorivand said:**
> Lo que podes hacer es restaurar los paneles por defecto de gnome.

```
gconftool-2 –recursive-unset /apps/panel
```Eso va a servir.

Saludos
Nacho

Gracias Nacho ya lo había echo y vuelve todo a un estado "anterior" pero... el hermoso menú sigue ahí :(

---

### Post by atari130xe on 2010-10-29
Listo lo solucioné así:

eliminé del panel: miniaplicación de indicadores (obvio que se llevó todo el sobrecito del chat, el ícono de volumen y cia.)
 a continuación hice lo siguiente:

Sistema---> Preferencias---> Aplicaciones al inicio

una vez ahí añadí lo siguiente:
```
gnome-volume-control-applet
```

reinicié sesión y me quedó solo el control del volumen además del indicador de red y la hora, solo lo que necesito.

quedó así:

[[IMG]http://img7.imageshack.us/img7/5255/pantallazo4h.png[/IMG]](http://img7.imageshack.us/i/pantallazo4h.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

