---
title: "Instalar KDE en Ubuntu"
date: 2008-09-03
forum: Software
---

### Post by fgl82 on 2008-09-03
Tengo una duda:

Quiero probar KDE en Ubuntu, PERO sin que me instale las aplicaciones de KUBUNTU. Es decir, me gustaría poder instalar un KDE lo más "limpio" posible, y probarlo de esa manera, para luego agregarle yo las aplicaciones que me interesen.

Por eso no me interesa el comando ese de instalar los paquetes de Kubuntu...

Sugerencias?

---

### Post by pol666 on 2008-09-03
mmm no estoy seguro pero yo en debian hice un


kde-core y me pidio sus dependencias

---

### Post by fgl82 on 2008-09-04
Pol. sos un capo. Hice más o menos lo que me dijiste y ¡¡¡anduvo de 10!!!

En realidad ahora tengo un problema más :D

mirá, yo lo que hice fue desinstalar todos los paquetes que dijeran "gnome+lo que sea", además de varios de GTK, el ubuntu-desktop y otros...

A la larga me quedé con un hermoso sistema con login en modo texto y que al darle "startx" te abría una consola en modo gráfico ¡jajajajaja!

Así que desde ahí hice lo de apt-get install kde-core, además del kdm y el adept. Anduvo todo joya, justo lo que quería, un KDE limpio, sin programas GTK ni tampoco QT, sólo los incluídos en el paquete core.

Bueno, mi problema es que no logro que me muestre en el escritorio la papelera de reciclaje :S

¿alguien tiene alguna idea? Ya googleé mucho pero para KDE no encuentro nada... todo lo que sale es el gconf-editor de gnome...

---

### Post by pol666 on 2008-09-04
en el Kcontrol no hay nada :S?

---

### Post by fgl82 on 2008-09-04
¡Yo no lo encontre! :S

---

### Post by jpmorelli on 2008-09-04
Acá tenés un tuto de como hacerlo.

Suerte !

[http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/]("http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/")

No te olvides de grabar el archivo que pone como "Trash.desktop"

Igualmente si no me equivoco al hacer boton derecho sobre el escritorio podes agregarlo desde una de las opciones de agregar programa o algo asi, ahora mucho no me acuerdo pero esta por ahi.

---

### Post by fgl82 on 2008-09-04
> **jmorelli said:**
> Acá tenés un tuto de como hacerlo.

Suerte !

[http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/](http://linuxfud.wordpress.com/2006/09/24/how-to-add-the-trash-can-to-your-kubuntu-desktop/)

¡Muchas gracias!

Lo pruebo y te aviso, quizá yo no lo encontré porque buscaba "trash bin" no sé por qué... :S

pd: uno esperaría que KDE, siendo tan configurable, tuviera una opción lista para hacer eso... :( Igual sigo contento, dentro de poco posteo el look en el thread abierto para tal fin, que el otro día se quejaban de qu no había de KDE :D

---

### Post by leo_rockway on 2008-09-04
Click derecho sobre kicker > Add applet to panel > trash. Eso te lo pone en la barra.

Si querés tenerlo como un icono en el escritorio: click derecho sobre el escritorio > create new > link to location (url) y le mandás trash:/ como dirección.

Perdón por las cosas en inglés, pero no sé como lo habrán traducido y mi KDE lo tengo en inglés. Prefiero dar las indicaciones en inglés a poner una traducción que pueda llegar a confundir.

---

### Post by fgl82 on 2008-09-05
> **leo_rockway said:**
> Click derecho sobre kicker > Add applet to panel > trash. Eso te lo pone en la barra.

Si querés tenerlo como un icono en el escritorio: click derecho sobre el escritorio > create new > link to location (url) y le mandás trash:/ como dirección.

Perdón por las cosas en inglés, pero no sé como lo habrán traducido y mi KDE lo tengo en inglés. Prefiero dar las indicaciones en inglés a poner una traducción que pueda llegar a confundir.

Leo, te agradezco pero eso ya lo había hecho y, por esas cosas de la vida, no me anduvo... al hacer eso no me cambiaba el ícono de lleno/vacío.
De todas formas me anduvo perfecto lo de crear un archivo de texto del tutorial que m,e dejaron más arriba y nombrarlo "Trash.desktop".

Ahora tengo mi flamante "KDE Pelado" :P y ya lo posteé en "Como se ve tu SO".

¡¡¡Gracias a todos!!!

pd: mi KDE tb está en inglés, siempre lo instalo así para poder buscar mejor en internet, siempre hay más info en inglés y mejor buscar sabiendo como se llaman las cosas que andar adivinando traducciones...

---

