---
title: "Problema compilando Kooka"
date: 2010-03-05
forum: Software
---

### Post by ramiro_md on 2010-03-05
Buenas gente, estaba configurando el escaner de la multifunción en mi Debian squeeze con KDE, y estaba compilando Kooka en la version 0.44 y a la hora de hacer el make devuvle el sigueinte error:
> "checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!".
Por lo que leí era que me faltaban las librerias de desarrollo del xorg.
Buscando en google encontre que eran estas: libxorg-x11-devel, pero hice un aptitude search y no me figuran en las repos. En otro blog me encontré con instalar las siguentes librerias: x-dev libx11-dev kdebase-dev. Las 2primeras las pude instalar pero kdebase-dev no me figura tampoco. 
COn lo que pude instalar volvi a tirar ./configure y el error persisitió. 
Dónde puedo conseguir las librerias faltantes ? 
Un saludo y gracias!

---

### Post by guillermolisi on 2010-03-05
Si las librerias estan entonces puede ser que no coincidan los paths donde el compilador las espera encontrar.

---

### Post by alfplayer on 2010-03-06
Si lo que falta es el código del servidor X por lo que encuentró en Synaptic están en el paquete xserver-xorg-dev (en Karmic).

---

### Post by ramiro_md on 2010-03-09
Gracias por la data, si bien n osolucioné el tema de la compilación reemplaze la función de kooka por Gimp je.
Un saludo!.

---

