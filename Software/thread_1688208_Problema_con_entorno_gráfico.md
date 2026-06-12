---
title: "Problema con entorno gráfico"
date: 2011-02-15
forum: Software
---

### Post by miriambe on 2011-02-15
Hola.. es la primera vez que escribo y estoy dando mis primeros pasos en éste sistema...
Tengo un equipo que ha interrumpido el suministro eléctrico por lo que al reiniciar no me permite ingresar a la interfaz gráfica..

al comenzar aparece la opcion de ingresar en los siguientes modos:
[I]Ubuntu, linux 2.6.31-20-generic-pae
[/I][I]Ubuntu, linux 2.6.31-20-generic-pae(recovery mode)
[/I]
al escoger cualquiera de las opciones aparece lo siguiente:
[I]exec:5 mountall:not found
init: mountall main process(544) terminated with status 2
filesystem check failed
a maintenance shell will now be started
Control-D will terminate this shell and re-try
root@server1:~#

[/I]El equipo está funcionando en una escuela y no puede(en lo posible) ser formateado... Alguna sugerencia ???

Muchas Gracias):P

---

### Post by asterix77 on 2011-02-15
¿Que versión de ubuntu usas?

Por lo que veo te aparece la terminal, pero no arranca el entorno gráfico. ¿que pasa si escribes en la terminal lo siguiente?

#startx

Lo anterior es un comando para iniciar el entorno gráfico, te dará más detalle de algún problema que tengas.

En lo personal no creo que tengas que formatear o reinstalar de nuevo.

Saludos

---

