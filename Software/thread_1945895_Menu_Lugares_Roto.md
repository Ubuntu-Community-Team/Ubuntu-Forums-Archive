---
title: "Menu Lugares Roto"
date: 2012-03-23
forum: Software
---

### Post by javierlinux1 on 2012-03-23
Buenas noches, tengo un problema con el menu "Lugares", en un equipo con Ubuntu 10.04, cuando trato de acceder a cualquiera de los directorios que lo integran sale un error que dice:

"No se puede abrir el lugar: <<file:///home/user/V%C3%deos>>"
"No hay ninguna aplicacion registrada para manejar este archivo."

Pense que era un erro de la codificacion de caracteres, por como
muestra "Video", pero para Documentos muestra el mismo error, y así para cada uno de los directios a los que se intenta acceder.

Abrí nautilus y en el panel de la izquierda seleccioné "Lugares" como vista y funcionan todos de manera correcta, no se que puede pasar en la parte del menu y no encunetro en los foros ninguna solucion adecuada.

Si alguien sabe, agradecido.

Javier

---

### Post by papibe on 2012-03-24
Hola.

No he visto ese error antes, pero tengo la impresión de que se desasoció la aplicación asociada a los directorios (así como hay aplicaciones asociadas a archivos mp3).

Si estoy en lo correcto, lo podrías corregir de la siguiente manera:
[LIST]
[*]Abre nautilus (en el peor de los casos lo puedes abrir desde un terminal como 'nautilus').
[*]Dale click con el botón derecho del mouse y selecciona el equivalente en español de 'Open With' o 'Open with another application'. Me imagino que es 'Abrir con...'.
[*]Se va a abrir una ventana nueva. Elige el equivalente a 'File Browser' como en esta [foto]("http://i.stack.imgur.com/PMYiY.png").
[*]Cierra nautilus y trata de abrir 'Lugares' otra vez.
[/LIST]
Ojala lo puedas resolver. Avísanos si necesitas más ayuda.
Saludos.

---

### Post by javierlinux1 on 2012-03-25
Hola, gracias por la respuesta, pero no ha funcionado.

El tema es que si yo abro nautilus, me voy a /home/usuario y tengo todo, se puede acceder a todo.
El problema está en hacerlo desde el menu Lugares de la barra superior de Menus, no desde el navegador de archivos.

Probé creando un panel nuevo, agregandole la barra de menu y nada, hace lo mismo. Las demas opciones del menu, Aplicaciones, Sistema y dentro de estas, funciona todo Ok, solo los "lugares" no funcionan.
Lo más extraño es que en un momento se podian usar, y de golpe, sin motivo aparente, comenzo este problema.
Sigo investigando

---

