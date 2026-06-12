---
title: "Sombra bajo los iconos"
date: 2009-06-09
forum: Software
---

### Post by Fisaulerod on 2009-06-09
Hola, uso gnome y nautilus, y me gustaría saber si se puede poner sombras bajo los iconos en el escritorio como sale en esta imágen:

[IMG]http://ubuntulife.files.wordpress.com/2009/06/karmix.jpg[/IMG]
[COLOR=YellowGreen]*Imágen de un tema de Gnome-Look*
[/COLOR]
Gracias de antemano.

---

### Post by CdK1 on 2009-06-09
Pueés veásmos, tienes "algunas" maneras de lograr sombras y transparencias:

La manera nativa de Gnome, esto es, activando *compositing_manager* del metacity, cómo? así:

Ejecutas gconf-editor

 *apps > metacity > general*“. Y habilitas “*compositing_manager*“:

La otra es usando cairo-compmgr:

apt-get install cairo-compmgr luego:

Aplicaciones>Sistema>Preferencias>Cairo Composite Manager y configuras

Y la otra, y más conocida, configurando compiz-fusion etc, etc, etc ;)

---

### Post by Fisaulerod on 2009-06-10
en que parte del administrador de compiz sale eso?

---

