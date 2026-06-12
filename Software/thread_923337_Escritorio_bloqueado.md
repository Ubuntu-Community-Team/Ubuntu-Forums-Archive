---
title: "Escritorio bloqueado"
date: 2008-09-18
forum: Software
---

### Post by nahuel_89p on 2008-09-18
Buenas gente, les cuento que instalé el ubuntu tweak, para realizar modificaciones basicas en ubuntu (entorno grafico, opciones varias) y despues de probar modificaciones (pormenorosas, nada del otro mundo) un rato con esa aplicacion desaparecieron los iconos del escritorio y resulta que el escritorio no responde a los clicks derechos (no se abre el menu que entre otras cosas permite crear lanzadores y cambiar el wallpaper). Además, si intento arrastrar algun icono al escritorio, este rebota... y por ultimo, otro sintoma es que el puntero no puede hacer selección en el escritorio; en resumen, esta bloqueado.
Volvi todo lo que toque (q tampoco fue mucho) en el tweak a como estaba antes, pero no hay caso. Creo que el detonante fue que activé la casilla "nautilus con privilegios de root" y "nautlius con wallpaper"...las desactivé pero todo igual.. de todos modos no estoy seguro que puede ser.
La barra que tengo en el escritorio no esta bloqueada, puedo cambiarla de lugar a gusto. Ah, y los screenlets funcionan bien.
¿que recomiendan? Leí que debería borrar algunas carpetas ocultas en el directorio personal... pero eso de arreglar a las "borradas" no me convence, por lo que espero una 2da opinion.

Edit:1) En la carpeta escritorio, en /home/xxxxx/, aparecen los iconos del escritorio. 2) Uso Emerald como decorador de ventanas, y Compiz como administrador de ventanas.

Gracias!

---

### Post by Aspergillus on 2008-09-18
mmm doy por sentado que estas en gnome asi que proba hacer esto

abris una terminal y pones 

gconf-editor

una vez que te abre el editor de configuracion de gnome vas a 

apps ---> nautilus ---> preferences

ahi en la derecha buscas "show_desktop" y fijate que el valor este tildado, si no lo esta tildalo

espero que te funcione

---

### Post by nahuel_89p on 2008-09-18
Sí estoy en gnome, y en efecto el valor ese está tildado.
Cuando se carga el escritorio, durante una fraccion de segundo, aparecen los iconos. Luego desaparecen.
Muy extraño, es como medio aleatorio el error :S, pero hay algo que se carga al principio que me bloquea el escritorio, y no hay ningun programa o daemon que se encargue de eso, bah, lo unico que instale fue el ubuntu tweak... lo voy a desinstalar a ver que onda.
gracias x la pronta respuesta.

edit: como era previsible, sigue igual.
Alguna otra idea?

---

### Post by magemco on 2009-08-20
A mi me pasó lo mismo que a vos, instale ese Tweak-ubuntu y molestaba con el manager-compiz, uno me ponia una cosa, después lo abria y no estaba la configuración, no toque mas nada y me bloqueo el escritorio, con solo tildar la opcion de show_desktop lo solucione y obvio que lo saque, pero bueno anda genial. Saludos.

---

