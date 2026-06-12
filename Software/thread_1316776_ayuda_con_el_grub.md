---
title: "ayuda con el grub"
date: 2009-11-06
forum: Software
---

### Post by santiago79 on 2009-11-06
hola gente necesito ayuda en algo con el nuevo grub2 nose como editarlo osea tengo kubuntu karmic y ubuntu karmic y en el menu de grub tengo las 2 opciones de kubuntu y después las de ubuntu

ahora lo que yo quiero es que primero me diga ubuntu y me carge ubuntu y después abajo este kubuntu y que diga kubuntu 
osea algo asi

UBUNTU KARMIC KOALA 9.10
UBUNTU KARMIC KOALA 9.10 RECOVERY
MENTEST
MENTEST
KUBUNTU KARMIC KOALA 9.10
KUBUNTU KARMIC KOALA 9.10 RECOVERY

algo asi o si se puede mas ordenado mejor en si primero ubuntu después kubuntu
muchas gracias espero no a verlos mariados 
muchas gracias por el tiempo

---

### Post by josecuervo86 on 2009-11-06
Podrías mostrar el archivo de configuración completo?

---

### Post by guillermolisi on 2009-11-06
El contenido de /boot/grub/menu.lst y pegalo en un mensaje asi lo vemos

---

### Post by pablo.s on 2009-11-06
No recomiendo editar el menú
de GRUB 2. Son modificaciones
muy sensibles y de todas formas
con cada update-grub se corre
peligro que se descomponga.
Por lo menos hasta que se lance
una herramienta gráfica para la
configuración.

El archivo de configuración principal
está en /boot/grub/grub.cfg pero
DE NINGUNA MANERA se debe editar.
Luego los archivos que se editan están
en /etc/grub.d y no sé con exactitud si
manejan el orden de los sistemas.

EDIT: me acordé del [URL="http://ubuntuforums.org/showthread.php?t=1221784"]post que redactó
Gabriel[/URL] (ya van muchas veces que lo
recomiendo) y en el post aclara que en
/etc/default/grub se puede cambiar el orden
pero del sistema por default.

---

### Post by guillermolisi on 2009-11-07
> **guillermolisi said:**
> El contenido de /boot/grub/menu.lst y pegalo en un mensaje asi lo vemos
Ahora que leo el mensaje de Pablo caigo en la cuenta de que se habla de Grub2 con lo cual mi sugerencia es invalida para el caso.

---

### Post by rojojuan on 2009-11-07
Me parece que este link te da la solución:

[http://damncorner.blogspot.com/2008/11/cambiar-orden-de-arranque-en-grub2.html](http://damncorner.blogspot.com/2008/11/cambiar-orden-de-arranque-en-grub2.html)

---

### Post by rubioo on 2009-11-07
Hola Santiago, yo pude modificar GRUB2 gracias a estas dos guias:
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") y [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275").
Estan en ingles, pero son faciles de entender.

---

### Post by santiago79 on 2009-11-08
muchas gracias por la ayuda ahora veo si puedo hacerlo lo único que quiero es acomodarlo 
después le comento como me salio

---

