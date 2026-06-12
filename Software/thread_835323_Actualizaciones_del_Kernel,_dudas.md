---
title: "Actualizaciones del Kernel, dudas"
date: 2008-06-20
forum: Software
---

### Post by atari130xe on 2008-06-20
Gente, resulta que tengo la pc funcionando bién, pero para variar al aparecer las actualizaciones del kernel, dejan de uncionar algunas cosas (ej: la resolucíon de pantalla -tengo el driver de Nvidia compilado-) alguien podría indicarme que hacer para que que no se actualicen? hace un par de días encontré un blog donde explicaban este inconveniente y daban unas instrucciones para mantener los driver funcionando después de cada actualización del kernel e inclusive como mantener esos drivers actualizados de manera "automática" pero lamentablemente por torpeza no hice el bookmark del sitio. :(

---

### Post by faktorqm on 2008-06-20
Yo actualice todos los kernels sin volver a instalar el driver de nvidia, tengo la version 71.XX creo, que es la que anda bien con mi placa gforce 4. La instale con el envy-ng, que es para ubuntu 8.04. Quiza por eso cuando actualizo el tipo lo auto-pone, o nada que ver?

De todas maneras, no tenes que pensar en no actualizar el kernel, tenes que pensar en como reinstalar el driver de nvidia facil, o sea, envy-ng.
Salu2!!

---

### Post by sergiom99 on 2008-06-20
a mi me pasaba en GG que los instale con envy y cada update de kernel los "rompia". Lo mismo me pasaba con los ALSA que tuve que instalar para la placa de sonido. 
En HH directamente uso los restricted drivers para nVIDIA y los nativos para el sonido y listo.

---

### Post by Mister X on 2008-06-20
La forma de que no se actualice un paquete es marcarlo como "retenido" (hold), tendrias que retener el paquete del kernel y de esta manera no se actualizaria mas, nada recomendable ya que dejas de recibir mejoras y correccion de bugs.

Lo mejor para tu situacion si no queres recompilar a cada rato, es tratar de mantenerte siempre dentro de la distribucion, sobre todo con los modulos del kernel.

---

### Post by sdennie on 2008-06-20
Si estas usando los drivers de nvidia de [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html), escribi un HOWTO en Tips & Tutorials para compilar el driver automáticamente despues de actualizar el kernel: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).

Si tenés algún problema con ingles, te puedo ayudar.

---

### Post by sergiom99 on 2008-06-20
@vor: bienvenido al foro local de Argentina!
esperamos contar con tu ayuda mas seguido por estos lados.

---

### Post by faktorqm on 2008-06-20
Digo yo no es mas facil hacer un ln -f entre las carpetas de kernel y kernel y listo?? Salu2!

---

### Post by sdennie on 2008-06-20
> **faktorqm said:**
> Digo yo no es mas facil hacer un ln -f entre las carpetas de kernel y kernel y listo?? Salu2!

Me parece que no va a funcionar por los módulos (pero con el firmware si).  La diferencia entre, por ejemplo, kernel -16.11 y kernel -19.42 es que los módulos no son compatibles.  Si hay una actualización y los módulos son compatibles no cambian la penúltima numero de la versión.

@sergiom99: Gracias.  :)

Saludos

---

### Post by luks911 on 2008-06-20
> **vor said:**
> Si estas usando los drivers de nvidia de [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html), escribi un HOWTO en Tips & Tutorials para compilar el driver automáticamente despues de actualizar el kernel: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).

Si tenés algún problema con ingles, te puedo ayudar.

Excelente, vor. Muchas gracias. Todavía no lo probé porque no quiero poner a bajar otro kernel. Pero va a ser genial para la próxima actualización.

OT: Voy a empezar a buscar algo similar para instalar un driver modificado de madwifi que uso, ya que a cada cambio de kernel debo volver a instalarlo. No es que sea complicado, pero si se puede automatizar, mejor. De hallar o hacer algo similar, ¿debería modificar este script (update-nvidia-grub) para que además de lo que hace ejecute otro script que instale el madwifi? Digo porque requiere varios pasos (make y make install). En fin, no jodo más con eso. Gracias de nuevo.

---

### Post by sdennie on 2008-06-20
> **luks911 said:**
> 
OT: Voy a empezar a buscar algo similar para instalar un driver modificado de madwifi que uso, ya que a cada cambio de kernel debo volver a instalarlo. No es que sea complicado, pero si se puede automatizar, mejor. De hallar o hacer algo similar, ¿debería modificar este script (update-nvidia-grub) para que además de lo que hace ejecute otro script que instale el madwifi? Digo porque requiere varios pasos (make y make install). En fin, no jodo más con eso. Gracias de nuevo.

Podés modificar el script para hacer eso sin problema.  Si estas usando make y make install, fijate en el Makefile para ver si hay una opcion para compilar con otro kernel y instalar en otro kernel.  Si no, vas a reinstalarlo en el kernel viejo.

---

### Post by atari130xe on 2008-06-21
> **vor said:**
> Si estas usando los drivers de nvidia de [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html), escribi un HOWTO en Tips & Tutorials para compilar el driver automáticamente despues de actualizar el kernel: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).

Si tenés algún problema con ingles, te puedo ayudar.

Gracias! no hay drama con el Ingles, lo manejo muy bien (cuestiones de familia jejeje), Congratulations dude! Good job! :lolflag:

---

### Post by MeduZa on 2008-06-21
> **vor said:**
> Si estas usando los drivers de nvidia de [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html), escribi un HOWTO en Tips & Tutorials para compilar el driver automáticamente despues de actualizar el kernel: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).

Si tenés algún problema con ingles, te puedo ayudar.

excelente aporte lo voy a probar ni bien tenga tiempo, de todas maneras muy util.

---

