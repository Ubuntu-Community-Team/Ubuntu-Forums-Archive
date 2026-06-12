---
title: "Deshacer instalación de driver privativo para tarjeta gráfica en Ubuntu 10.10"
date: 2010-12-29
forum: Software
---

### Post by Dago_Ô on 2010-12-29
Hola a todos...

Tengo el siguiente problema.  Acabo de instalar Ubuntu 10.10 en forma limpia (vengo usando Ubuntu desde la 8.04) y luego de terminar las actualizaciones oficiales, le hice caso a lo que decía en [este blog]("http://ubuntulife.wordpress.com/2010/10/20/cosas-a-hacer-despues-de-instalar-ubuntu-10-10-maverick-meerkat-2/") en relación a cosas que hacer luego de terminar la instalación, en las cuales decía que se instalaran los driver oficiales de ATI/AMD.  Me pareció interesante poder ver el rendimiento de estos drivers e ejecuté los comandos.
El problema es que ahora no me reconoce el dirver y no puedo usar COMPIZ y por lo tanto el lanzador Docky.
Intenté revertir la instlación con el comando ```
apt-get remove fglrx
```, pero no funcionó.
Me gustaría volver a la configuración inicial, ya que funciona bien.
Mi equipo es un Acer Asipre 5050 con una tarjeta gráfica ATI Radeon Xpress 1100 (el sistema me la reconoce como una Xpress X200M).

Ahora ya se que no hay que arreglar lo que no está malo.
Saludos y gracias desde ya

---

### Post by Maciett on 2010-12-29
[SIZE=2]Hola,

Según te entiendo instalaste un driver privativo, para sacarlo ve a Sistema-->Administración-->Controladores Adicionales y seleccionalo, luego le das deshabilitar/eliminar y dejar el driver libre en vez de ese. Reinicias y debería quedar como al principio.

Saludos
[/SIZE]

---

### Post by Dago_Ô on 2010-12-29
> [SIZE=2]para sacarlo ve a  Sistema-->Administración-->Controladores Adicionales y  seleccionalo, luego le das deshabilitar/eliminar y dejar el driver libre  en vez de ese. Reinicias y debería quedar como al principio.[/SIZE]

Intenté eso, pero la ventana me indica que no existe driver privativo instalado.  De hecho, se me instaló el Catalyst Control Center, pero me sale un error diciendo que no se pudo encontrar un dispositivo adecuado.  Me recomienda que use el comando *aticonfig* , pero al hacerlo me sale un mensaje similar, que no se encuentra un dispositivo soportado.

---

### Post by asterix77 on 2010-12-30
Tengo en mi latptop esa misma tarjeta, si mal no recuerdo en jaunty me funcionaba con el driver de ATI, ya en versiones posteriores de Ubuntu creo que salió un driver mantenido por la comunidad, intenté muchas veces tanto en jaunty como en las versiones posteriores, instalar el driver de ATI, y simplemente no lo pude hacer o solo lo pude hacer a medias. Nunca me resultó al 100%.

Conclusión: me funcionó mejor el driver libre, por lo que desistí de la idea del driver ATI


De todos modos he agregado el siguiente repositorio para tener los controladores de mi tarjeta más actualizado. Quizás te convenga agregarlo. 


[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) maverick main

Saludos

---

### Post by Dago_Ô on 2011-01-10
disculpa por la demora de la respuesta.
En efecto, fue un parto el tema de los drivers de ATI, así que corté por lo sano y solo estoy utilizando las versiones libres que funcionan bastante bien.

Gracias

---

