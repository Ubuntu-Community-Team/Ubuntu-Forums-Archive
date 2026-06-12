---
title: "Resolución 800x600 inmodificable..."
date: 2009-08-08
forum: Software
---

### Post by CarlosRuiz on 2009-08-08
Holap:

Instalé Ubuntu 8.04 como siempre lo hago, pero esta vez la resolución por defecto era de 800x600 en lugar de mi favorita:1024x768.

Al igual que en las veces anteriores, traté de cambiarla escribiendo en la consola:
 **sudo dpkg-reconfigure xserver-xorg** 

...pero por alguna razón esta vez sólo aparecen opciones para modificar el teclado, y NO la resolución de la pantalla.

Otra cosa extraña es que mientras Ubuntu se está cargando, el sistema me avisa que la pantalla está en baja resolución y me da varias opciones, pero aunque las cambio para que queden como me gusta, no pasa nada... y si voy a Sistema -> Preferencias -> Resolución de Pantalla, sólo aparecen las opciones 800x600 y 600x400.

Help, plisss!! :confused:

Saludooos :(

---

### Post by gmunioz on 2009-08-10
Hola car....:

¿Qué tarjeta gráfica tienes?

Si tienes Ati o Nvidia, debes

instalar los módulos privativos

para obtener todas sus prestaciones.

Si ya estan instalados, puedes editar

el archivo xorg.conf para agregarle

como único modes en todas las profundidades

de color 1024 x 768

---

### Post by Patriciologico on 2009-08-15
Estoy usando Ubuntu Karmic Koala (testing) y tengo el mismo problema con una tarjeta

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) que en jaunty funciona en 1152x864

En Karmic, no tengo el archivo xorg.conf, entiendo que esto es normal ya que el nuevo kernel funciona de forma diferente (pero no me aclaro)

¿Alguna idea?

---

### Post by CarlosRuiz on 2009-08-18
Holap:

Una solución que encontré es:
[B][B]sudo displayconfig-gtk

[/B][/B]Sólo hay que ingresar el modelo del monitor y cambiar la resolución... xD

Saludooos :P

---

### Post by Patriciologico on 2009-08-18
Creo que cometi un error, no debi mezclar un problema de una version 9.10 alpha, con el tuyo que es de la 8.04. 

Efectivamente, lo que propones funciona, pero en versiones antiguas. En cambio lo que he podido comprender del problema de 9.10 alpha 3, pasa por el nuevo kernel y las mejoras que se trabajan en el driver de intel, que ya en Jaunty ha dado problemas sin mejoras (de aceleracion, no de resolucion en este caso)

Por ejemplo el comando sudo dpkg-reconfigure xserver-xorg que en jaunty hace bien poco, en karmic ya no sirve para nada. y olvidense de editar xorg.conf, que no existe.

Saludos!

---

