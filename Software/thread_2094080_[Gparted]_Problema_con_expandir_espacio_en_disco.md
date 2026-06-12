---
title: "[Gparted] Problema con expandir espacio en disco"
date: 2012-12-12
forum: Software
---

### Post by reLlene on 2012-12-12
Resulta que al final de mi disco me estan sobrando unos 15.32GiB, aparte del MiB que se encuentra más arriba xD pero es que **NO puedo expandir** mi /sda6 de 50.15 a todo lo que aguante (me refiero hasta el punto de valerse de los 15.32GiB que tiene contiguo y sin asignar).
 
 Dejo un print de cómo se ve la situación

[IMG]http://i46.tinypic.com/161e39d.jpg[/IMG]

Y el problema a la hora de expandirlo :(

[IMG]http://i47.tinypic.com/2zexogy.png[/IMG]

Saludos.

---

### Post by dirty fingers on 2012-12-12
por lo que se ve en la captura estas intentando redimencionar una partición que esta montada; cosa que no es posible.

---

### Post by reLlene on 2012-12-13
> **dirty fingers said:**
> por lo que se ve en la captura estas intentando redimencionar una partición que esta montada; cosa que no es posible.

 MUY cierto, habia olvidado que lo habia hecho con el liveCD de Gparted porque debia de encontrarse desmontada tal unidad para poderla modificar, pues lo hice y resulto de la misma manera, no resultó!! algún consejo? :(

---

### Post by EnriqueK on 2012-12-13
Por lo que aprecio estás usando muy poco espacio en /home, por lo que resulta ideal para respaldarla en un pendrive , borrar esa partición  extendida , de esa manera todo será un area sin asignar por lo que podrás aprovechar de darle mas espacio a la sda1  ya que hoy en día  10 Gb es poco, diría que esta no debe ser menor a  15 Gb, luego recreás la extendida, creas las logicas y repones la parición /home 
Leete el siguiente enlace en el que trato en detalle un caso mucho mas complejo, pero conceptualemente muy similar.
[http://ubuntuforums.org/showthread.php?t=1759591](http://ubuntuforums.org/showthread.php?t=1759591)

---

### Post by reLlene on 2012-12-19
> **EnriqueK said:**
> Por lo que aprecio estás usando muy poco espacio en /home, por lo que resulta ideal para respaldarla en un pendrive , borrar esa partición  extendida , de esa manera todo será un area sin asignar por lo que podrás aprovechar de darle mas espacio a la sda1  ya que hoy en día  10 Gb es poco, diría que esta no debe ser menor a  15 Gb, luego recreás la extendida, creas las logicas y repones la parición /home 
Leete el siguiente enlace en el que trato en detalle un caso mucho mas complejo, pero conceptualemente muy similar.
[http://ubuntuforums.org/showthread.php?t=1759591](http://ubuntuforums.org/showthread.php?t=1759591)

 **EnriqueK** A ver si entiendo lo que has hecho en ése topic que me pasaste...Has creado por cada particion del disco un único archivo .tar.gz (comprimido) para luego volcarlo de vuelta pero con las particiones en otros lugares? es asi?
[LEFT] Por cierto, cómo puedo hacer para compartir mi /home independientemente de mis distintos distros cómo te ha dicho el compañero **z37a **en ése mismo topic? 
 :S
[]("http://ubuntuforums.org/member.php?u=494828")[/LEFT]

---

### Post by EnriqueK on 2012-12-20
Claro, si a las particiones les ponés etiquetas, al correr un LiveCD de Ubuntu por ejemplo, vas a ver que cuando las montás, estas  aparecen en /media como carpetas comunes y corrientes, de lo que se trata entoces es el de empaquetar en tar o en .tar.gz si no tienes mucho espacio  y luego redefines la nueva tabla de particiones, les ponés las mismas etiquetas y descommprimís , así de simple es la cosa.
Respecto al comentario, no respondí por que no hacía al tema, de todas maneras, soy de la opinión que eso de tener /home separada es anacrónico, sobretodo cuando se tienen tantos entornos que se van probando hasta dar con el mas apopiado, por eso pongp a /home en ls particiñon raíz / y los datos , que al final de cuentas son los únicos que valen la pema compartir, los tengo en otra particióm. Te dejo un par de enlaces donde se tratño este tema.
[http://www.espaciolinux.com/foros/sistema/separar-home-archivos-home-configuraciones-t50951.html](http://www.espaciolinux.com/foros/sistema/separar-home-archivos-home-configuraciones-t50951.html)
[http://www.espaciolinux.com/foros/instalacion/manjaro-home-enlazada-problemas-con-suprimir-t50996.html](http://www.espaciolinux.com/foros/instalacion/manjaro-home-enlazada-problemas-con-suprimir-t50996.html)

---

### Post by EnriqueK on 2012-12-20
Claro, si a las particiones les ponés etiquetas, al correr un LiveCD de Ubuntu por ejemplo, vas a ver que cuando las montás, estas  aparecen en /media como carpetas comunes y corrientes, de lo que se trata entoces es el de empaquetar en tar o en .tar.gz si no tienes mucho espacio  y luego redefines la nueva tabla de particiones, les ponés las mismas etiquetas y descommprimís , así de simple es la cosa.
Respecto al comentario, no respondí por que no hacía al tema, de todas maneras, soy de la opinión que eso de tener /home separada es anacrónico, sobretodo cuando se tienen tantos entornos que se van probando hasta dar con el mas apopiado, por eso pongp a /home en ls particiñon raíz / y los datos , que al final de cuentas son los únicos que valen la pema compartir, los tengo en otra particióm. Te dejo un par de enlaces donde se tratño este tema.
[http://www.espaciolinux.com/foros/sistema/separar-home-archivos-home-configuraciones-t50951.html](http://www.espaciolinux.com/foros/sistema/separar-home-archivos-home-configuraciones-t50951.html)
[http://www.espaciolinux.com/foros/instalacion/manjaro-home-enlazada-problemas-con-suprimir-t50996.html](http://www.espaciolinux.com/foros/instalacion/manjaro-home-enlazada-problemas-con-suprimir-t50996.html)

---

