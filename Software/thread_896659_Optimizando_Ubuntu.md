---
title: "Optimizando Ubuntu"
date: 2008-08-21
forum: Software
---

### Post by fgl82 on 2008-08-21
¡Hola!

Se me ocurrió buscar por internet formas de optimizar ubuntu, en cuanto a su performace general.

Encontré varias páginas que daban tips sobre qué servicios son factibles de ser eliminados en el startup, de manera de acelerar el booteo y además no tener recursos ocupados al divino botón.

Sin embargo, no encontré que hicieran una real diferencia en mi PC.

Por eso, me gustaría iniciar un thread (que me parece tiene potencial de sticky) sobre tweaks probados por alguno de nosotros, que realmente arrojen una diferencia de performance en nuestro bienamado SO, ya sea en ahorro de memoria, reducción de tiempo de booteo u otro, como por ejemplo, reducción del uso de la partición swap. no sé, ahora no se me ocurren más cosas a "afinar" pero seguro debe haber.

Ojo, me refiero a tweaks algo más complicados que "usa XFCE en lugar de Gnome"

Acá es donde yo debería empezar aportando un tweak, pero como ya dije, los que encontré no marcaron diferencias en la performance de mi sistema, así que dejo que los grossos en serio (LeoRockway? Faktor? están ahi?) aporten sus ideas.

¡Saludos!

---

### Post by Hei Ku on 2008-08-21
Desactivar el tracker :)

---

### Post by fgl82 on 2008-08-21
El tracker es lo que te indexa los archivos?

Eso lo corrí hace poco :lolflag:

hice mal?

---

### Post by pol666 on 2008-08-21
yo desactivo servicios y programas de inicio en la sesion, despues saco las consolas virtuales (las redusco de 8 a 4).. tambien saco del fstab las particiones que no quiero montar para que inicie mas rapido. Saco el splash de nvidia y el gdm para ahorrar unos segundos.

---

### Post by fgl82 on 2008-08-21
La idea del thread es especificar un poco más Pol, no sé, por ejemplo, aclará qué servicios desactivás así si alguien tiene una configuración similar a la tuya le sirve loque ponés.

Es una sugerencia bah, esa era mi idea al iniciar el thread, no te me vayas a ofender :)

---

### Post by fiddler616 on 2008-08-21
Perdonen mis tildes--que no tengo teclado internacional.
Ayuda un poco borrar programas no usadas. Por ejemplo, como uso el internet para mis correos electornicos, borre Evolution.
Tambien ayuda si no tienes efectos del desktop, o sea elegir "No Desktop Effects" en vez de "Normal Desktop Effects" o "Extra Destkop Effects".
...No son muchos, pero ayudan un poco...

---

### Post by pol666 on 2008-08-21
no como me voy a ofender. ME gustaria detallarte un poco mas pero ahora estoy con otro disco, otro ubuntu, Cuando recupere lo mio te cuento que es lo que saque exactamente.

---

### Post by sdennie on 2008-08-21
Podés usar preload ([http://sourceforge.net/projects/preload):](http://sourceforge.net/projects/preload):)

```

sudo apt-get install preload

```

Fijate en /etc/preload.conf por mas información.

Si no te gusta preload, [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651) ayuda a mucha gente y hace cosas parecidas.

Si tenés una laptop con nvidia y compiz: [ HOWTO: Improve NVidia Laptop Graphics Performance]("http://ubuntuforums.org/showthread.php?t=828369")

Tambien, con nvidia: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

Mas, si tenés un montón de RAM, podés montar partes del sistema como tmpfs.  Yo solo lo hago por ahorrar la batería pero acá tenés un ejemplo: [http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive)

---

