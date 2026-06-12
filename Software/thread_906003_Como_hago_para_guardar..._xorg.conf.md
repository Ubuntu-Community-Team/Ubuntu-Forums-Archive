---
title: "Como hago para guardar... xorg.conf"
date: 2008-08-30
forum: Software
---

### Post by GambitCba on 2008-08-30
Como hago para guerdar xorg.conf
resulta que le pongo una resolucion a la pc pero cuando reinicio me vuelve a la que tenia cuando recien lo instale... Estoy usando para cambiar la resolucion Nvidia X SERVER SETTINGS...

Saludos.

---

### Post by pol666 on 2008-08-31
Vieja, leiste lo que te comente en el post que abriste antes???> 

**Te cuento capas que cuando reinicias se te vuelve a la otra resolucion. Lo que tenes que hacer es para quedarte tranquilo...**


1- anda a sistema>administracion>NVIDIA x server settings.
2- Anda a la solapa que cambia la resolucion y elegi la que quieras.
3- Clickea en Save to X configuration File
4- y pone guardar[B]

Si te sale algo de que no puede escribir el fichero[/B]

3- Clickea en Save to X configuration File
4- Entra en Show Preview
5- Copia todo el texto
6- Abri una terminal y escribi sudo gedit /etc/X11/xorg.conf
7- Borra todo lo que este escrito y copia el texto de la preview.
8- Guardas y listo

**Consejo extra por si no sabias**

abri un terminal y escribi *sudo apt-get install compiz-settings-manager fusion-icon emerald*
Despues Podes activar los efectos de escritorio en sistema>preferencias<apariencia
y modificar los plugin en sistema>preferencias>configuracion avanzada de efectos de escritorio

Podes agregar en sistema>preferencia>sesiones  el programa fusion-icon, que te permite activar o dsactivar los efectos desde el systray y ademas te deja elegir entre emerald o metacity como bordes de ventanas.

¬¬... pues...

---

### Post by faktorqm on 2008-08-31
más facil, apreta ALT + F2, escribi "sudo nvidia-settings" (sin comillas) hace todo y te lo graba sin problemas. salu2!

---

