---
title: "[Iconos] No se cambian en el panel"
date: 2009-06-26
forum: Software
---

### Post by rubioo on 2009-06-26
Hola, sigo molestando ....

 En plena modificación de mi escritorio, me di cuenta que hay algunos iconos
 que no se cambiaron (se quedaron como en el tema que tenía antes).
 Y quería saber si se podían cambiar, así dentro de todo queda un poco mejor
 mi escritorio :)
 
 Dejo una imagen de los iconos que no se cambiaron :) 
 
 Los iconos son los del Emesene y GUFW, y en el menú lugares son Documentos,
 Música, Imágenes y Vídeos.

  [[IMG]http://img269.imageshack.us/img269/5203/pantallazorpv.th.png[/img]](http://img269.imageshack.us/i/pantallazorpv.png/)

 [[IMG]http://img514.imageshack.us/img514/7656/pantallazor.th.png[/IMG]](http://img514.imageshack.us/i/pantallazor.png/)

---

### Post by staar on 2009-06-26
mirá, en algunas aplicaciones es muy difícil cambiar el ícono del tray, porque viene bastante 'metido' dentro de ella, sobre todo cuando ese ícono puede cambiar de estado (network-manager es la excepción, pero porque viene muy integrado al sistema), y la inmensa mayoría de los packs ni se gastan en tratar de modificarlos, supongo que se podrá cambiar, pero ni idea como...

los íconos de carpetas que no se te cambiaron, supongo será porque falta, o el ícono de carpeta en ese tamaño (creo que ese es 16x16), en ese caso crealo como te dije en el otro thread, o porque faltan los enlaces simbólicos necesarios, en ese caso podrías fijarte en un pack que si los cambie, y compararlo con el que usas ahora, para ver que enlaces faltan...

saludos

---

### Post by rubioo on 2009-06-26
Los iconos son Mashup, y dentro de la carpeta no tienen las carpetas con
 los distintos tamaños.
 
 Encima dentro de la carpeta hay un icono que se llama 'emesene_tray-icon'...

 Lo de los enlaces simbólicos como es :confused:

      Saludos

---

### Post by rubioo on 2009-06-26
El tema de los iconos del menú Lugares lo pude solucionar.
 
 [http://http://ubuntuforums.org/showpost.php?p=5964458&postcount=544]("http://http://ubuntuforums.org/showpost.php?p=5964458&postcount=544")

 Ahora solo me quedan los iconos del panel...


 EDIT: para cambiar el icono de GUFW modifique el archivo
      
 > /usr/share/gufw/variables_paths_messages.py

 En la parte de PATHS, ICONS.

 Ahora solo queda el icono del emesene mas un nuevo problema que aparecio recien (porque reinstale los iconos Mashup) ¬¬
 En el applet del panel que muestra las ventanas abiertas, cuando abro nautilus me nuestra un icono azul (muy feo). Si alguien sabe como
 cambiarlo, se lo agradezco :)

           Saludos

---

### Post by staar on 2009-06-26
por lo que encontré hurgando en el deb de emesene, los íconos del tray están en /usr/share/python-support/emesene/themes/*tema* (por defecto trae 3 temas), pero no se cuales tendrías que cambiar...

saludos

---

### Post by rubioo on 2009-06-26
Entre a la carpeta donde están los temas de Emesene y cree uno con los
 iconos como quiero que estén, pero no se cambiaron :(

 Igual, no me molesta tanto como está ahora.
 Lo que si quisiera cambiar es el icono de nautilus que aparece en el panel.
 Porque desde hoy a la tarde que desinstale los iconos Mashup, para instalar
 los iconos Mashup-5 (desde gnomelook), quedo así el icono y hasta ayer a 
 la noche estaba bien. Si quieren ver como estaba pasen por [acá]("http://ubuntuforums.org/showthread.php?t=1134824&page=21#210")

 Dejo una imagen de como se ven ahora.

      Gracias y espero que puedan ayudarme :D

---

### Post by staar on 2009-06-26
para lo primero, cambiaste el tema en el emesene, no?

para lo segundo, si es una nueva versión del pack, capaz que el autor decidió cambiar el ícono, buscalo en la carpeta del pack y reemplazalo por el anterior (fijate de reemplazar el ícono original, no alguno de los enlaces hacie este), la verdad, ni idea como se llama, ni en que subcarpeta está...

saludos

---

### Post by rubioo on 2009-06-26
Sisi, cambie el tema desde Opciones > Preferencias > Tema

 Gracias :D
 El archivo que baje tiene 5 pack de iconos (Mashup 1, 2, 3, 4 y 5) y estoy
 usando el 1 (que era el que tenía ayer).
 El archivo se llama "system-file-manager.png" y ya esta como lo tenía antes

 Ahora solamente queda el icono del Emesene, aunque no tengo apuro en
 cambiarlo.

          Muchas gracias staar :KS

  Saludos

---

