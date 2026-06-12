---
title: "[SOLVED] Archivos Borrados"
date: 2009-07-26
forum: Software
---

### Post by jawifi01 on 2009-07-26
Bueno ahora si, les comento mi problema:

Tengo una PC de escritorio con Ubuntu 9.04, donde tengo virtualizado un Windows XP mediante SunVirtualbox, anoche mientras configuraba diferentes cosas del equipo (AWN, música, etc) tenía corriendo el virtualbox con XP 32 para ir haciendo pruebas tambien, y se me ocurrio seleccionar una carpeta para compartir entre Win y Ubuntu. Hasta ahi todo bien, hasta que desde Windows le di BORRAR a una carpeta que enlazaba con otra:

Particion /dev/sda2 de 100 gb montada en /datos en ubuntu con varias carpeta de datos en general y dos enlaces, uno "Enlace a Fotografia" y otro igual a Musica, las carpetas Fotografia y Musica estan ambas en esa misma partición, y yo le pedi borrar el "Enlace a Fotografia", cuando lo estaba haciendo le di cancelar y al volver a entrar a ese enlace o a la carpeta, en ambos casos la muestra vacia!!!!! y tenia fotos familiares importantisimas!!!!

Reinicie el equipo en Ubuntu, con algunos LiveCd, de varias maneras mas y la carpeta Fotografia sigue apareciendo vacia absolutamente. 

Para no hacer ningun desastre mas arranque con  RIP Linux y puse a correr la orden

foremost -v -t all -q -i /mnt/sda2 -o /mnt/sda3/rec

y se paso toda la noche laburando, pero no muestra nada.

Si alguien tiene alguna otra "receta" mejor, escucho sugerencias, ya que recupero las fotos o me divorcio!!!!!!!!!

Saludos

Juan

---

### Post by sergiom99 on 2009-07-26
Ya te guiaron bastante en la lista, pero tambien hay una utilidad que se llama photorec.
Fijate en estos links: [http://ubuntuforums.org/search.php?searchid=62267082](http://ubuntuforums.org/search.php?searchid=62267082)

Suerte!

---

### Post by jawifi01 on 2009-07-28
Gracias, usé esta utilidad y recuperé todo, solo que me cambio los nombres a combinaciones de numeros y letras, pero lo importante es que está todo.

Gracias

Juan

---

### Post by sergiom99 on 2009-07-29
buenisimo! me alegro, zafaste del divorcio entonces. ;-)

---

