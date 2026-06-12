---
title: "&quot;Interferencia&quot; al reproducir video (Ubuntu 9.04)"
date: 2009-10-09
forum: Software
---

### Post by ivancito on 2009-10-09
Hola, mi nombre es Iván, soy nuevo en Linux y más nuevo aún en el foro.
Recientemente instalé Ubuntu 9.04 en mi pc  (Athlon x2 4200 + Asus m2a-vm, lamentablemente con video ati x1250 integrado) y no tengo mayores problemas (el post es desde linux :P) salvo el siguiente: al reproducir video .avi en tamaño full screen veo "interfercias" y una desagradable linea diagonal q afecta los frames.
Para ser mas explicito la velocidad de reproducción es normal, el sonido no esta defasado pero la imagen se ve con "basura".
Estado de mi intalación: "brand new" :P... borre los reproductores q vienen, instalé mplayer, corri el upgrade, instalé los codecs, paquetes restrictivos, uso el driver de linux p mi placa de video (me iamgino q por ahí viene la historia).
Probé cambiando los "available drivers" desde el mplayer pero no cambia mucho la situación.
Si alguno se le ocurre alguna idea mil gracias ya q mi objetivo es ir dejando relegado winchot.

Saludos

p.d: espero no haber faltado a ninguna "buena costumbre" del foro.
p.d2: alguien sabe proq cdo maximizo las ventanas se me torna blanca la barra dnd están los botones de cerrar, maximizar y minimizar?

---

### Post by Mauro22 on 2009-10-09
Eso lo hace con el mplayer?


Probá con el VLC


Aplicaciones -> Accesorios -> Terminal y pones:

```
sudo apt-get install vlc
```

luego tu contraseña y probá con ese...

---

### Post by ivancito on 2009-10-09
Hola, gracias por responder... Lamentablemente Instalar VLC no me soluciona el problema, puede ser q ande un toque mejor, y cambiando las salidas (o drivers de salida)  varíe un toque pero sigue teniendo defectos. Una prueba q hice ayer fue instalar la versión 8.04 para poder cargar los controladores de ATI, lo hice muy a lo catinga y resulto que se seguía viendo mal pero sin la ralla diagonal q cruza el monitor...

---

