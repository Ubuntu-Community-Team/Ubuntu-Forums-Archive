---
title: "[SOLUCIONADO] Cambiando permisos de usuario-grupo-otros"
date: 2009-07-18
forum: Software
---

### Post by ppellet on 2009-07-18
Estimados

Hace tiempo que no me dedicaba a develar los misterios que Ubuntu tiene para mi, esto significa, "meter mano" por aquí y por allá, instalar softwares, desintalarlos, etc. para finalmente "dejar la escoba" con mi sistema. Todo se inicio cuando cambié el skin de VLC, al reiniciarlo no volvió más, sólo lo podía correr desde consola. En fin, busqué por aquí y por allá y hasta el momento no pude solucionar este problema.

Pero, ya no importa. Intenté una cosa nueva, al menos para mi: cree un nuevo usuario con todos los privilegios. Y como ya tenía "casi" todas las aplicaciones que me interesan comencé a trabajar con este nuevo usuario. Además, ahora funciona VLC sin problemas, claro que, con la apariencia de siempre.


[LIST]
[*]Primero moví todas las carpetas desde el antiguo usario hacia el nuevo usuario. Eso sí, no moví las carpetas que contienen las configuraciones del usuario para las aplicaciones, las que están ocultas. Entonces, como me cambié de usuario, tengo todo de cero, en limpio, con la configuración original.
[/LIST]
  
[LIST]
[*] Todo venía bien hasta que... quise cambiar los permisos de usuario-grupo-otros para poder leer/escribir borrar, etc. Resulta que los archivos y carpetas dicen que el propietario es... el antiguo usuario y no el actual nuevo usuario.
[/LIST]
 
[LIST]
[*] Aprendí a cambiar los permisos con *chown* pero para uno o para varios archivos dentro de una carpeta, o para varias carpetas dentro de un directorio, pero no sé como hacer esta pega para todos los directorios, sus carpetas y archivos de una sola vez. Dado que tengo muchos archivos y carpetas no puedo estar casi de a uno por uno cambiándoles sus permisos.
[/LIST]
 
:confused:La pregunta es: ¿cómo puedo cambiar los permisos para todos los directorios y sus archivos de una sola vez, o sea, re-asignarlos desde el usuario antiguo al usuario nuevo?...


Me despido agradeciendo de antemano a quienes me puedan colaborar con este problema.

Saludos a todos,

---

### Post by Carlos C on 2009-07-18
Hola. Para cambiar de propietario puedes hacerlo de la siguiente manera:
```
chown <propietario>:<grupo> <archivo>
```Si lo que quieres es hacerlo de manera recursiva puedes añadir el parametro "-R".

Por otro lado, cuando desees cambiar los permisos a los archivos al interior de tu home, lo que puedes hacer es usar el comando chmod:
```
sudo chmod 644 /home/nombreusuario -R
```Esto dará a todos los archivos en el interior de tu home los permisos: rw-r--r--.

En caso de que necesites permiso de ejecución escribes:
```
sudo chmod 744 /home/nombreusuario -R
```Que equivale a los permisos : rwx-r--r--

En la Guía Ubuntu tienen una tabla bastante clara para entender lo de los números y los permisos, eso en caso de que no lo tengas claro, si no es así, que sirva para otros :):

[http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros#Cambio_de_permisos](http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros#Cambio_de_permisos)

También puedes usar nautilus para cambiar de propietario y de permisos. Basta que lo corras con sudo:
```
sudo nautilus
```Pero en ese caso es preferible y mucho más intuitivo configurar nautilus para que te muestre el menú avanzado de permisos de archivo:

[[IMG]http://img195.imageshack.us/img195/1411/propiedadesdefile.th.jpg[/IMG]]("http://img195.imageshack.us/i/propiedadesdefile.jpg/")

Acá puedes ver como hacerlo:

[http://blockdeubuntu.blogspot.com/2008/07/habilitar-el-men-avanzado-de-permisos.html](http://blockdeubuntu.blogspot.com/2008/07/habilitar-el-men-avanzado-de-permisos.html)

Saludos.

---

### Post by ppellet on 2009-07-19
Carlos C

"Te mandaste las partes", voy a probar las tareas que me indicas y luego les cuento o escribo si tengo dudas.

Me surgió una pregunta cuando vi el término "recursivo". Se refiere a que, ¿si cambio los permisos a una carpeta usando la opción recursiva, esto hará que se repita esta misma acción en cada una de las carpetas contenidas y sus archivos?...

Saludos a todos,

[**editado por mi - SOLUCIONADO**]
*Acabo de hacer las pruebas y efectivamente pude cambiar los permisos.

*Al incluir la opción recursiva, ésta cambia todo dentro de la carpeta.

*A pesar de lo anterior, el cambio completo lo hice usando la forma gráfica, esto es, usando *sudo nautilus* (antes, configuré nautilus para que me mostrara el menú avanzado, siguiendo lo indicado por Carlos C).
-Luego, me posicioné en la carpeta cuyos permisos quería cambiar, (la del usuario y todo su contenido: /home/usuario/),
-botón derecho,
-pestaña permisos,
-seleccioné los permisos que quería, y 
-clic al final abajo, en la opción: "Aplicar permisos a los archivos contenidos".

Todo resultó bien. Muchas gracias Carlos C por tu ayuda.

ppellet

---

