---
title: "Reproducir carpetas con Aimp (Wine)"
date: 2009-08-22
forum: Software
---

### Post by guidito73 on 2009-08-22
Buenas gente...

Les comento: actualmente uso Wine para reproducir música en la PC (es el que mejor sonido me da), hace poco le hice un script que encontré por ahí para agregarlo como opción para que los archivos de audio se abran por defecto con Aimp a través de Wine.

El tema es que no puedo hacer que Aimp reproduzca una carpeta eligiendo el script desde el menú contextual (el script se llama startwine). Es decir, click derecho en la carpeta que contiene los discos, elijo 'startwine', pero no pasa nada. Obviamente el script funciona sólo para los archivos individuales.

Alguien me puede dar una mano para poder reproducir las carpetas enteras directamente desde el menú contextual?

---

### Post by nopersona on 2009-08-22
Uf, si aimp te da mejor sonido que amarok, me hago monje.

---

### Post by Hei Ku on 2009-08-22
> **nopersona said:**
> Uf, si aimp te da mejor sonido que amarok, me hago monje.

Si no tenes algo on-topic para aportar, por favor evita los comentarios innecesarios.
Por si te haces monje: [http://es.wikipedia.org/wiki/Voto_de_silencio](http://es.wikipedia.org/wiki/Voto_de_silencio)

guidito: seria bueno que pusieras el script que usas. 
Y otra cosa, entrar a un foro de linux, decir que sus programas suenan mal y ademas pedir ayuda, da muestra de una esperanza en la naturaleza humana envidiable

---

### Post by guillermolisi on 2009-08-23
Cualquier comentario inespecifico al asunto del thread, que no tenga la intencion de indagar en el problema, buscar converger en alguna solucion, ayudar a la cuestion planteada, sera moderado.

---

### Post by guidito73 on 2009-08-23
A ver, a ver... que saltaron un par de tapones de más!

Uso Aimp por la relación calidad de sonido/uso de memoria. No sé, simplemente me resulta (hasta ahora) lo mejorcito. Sí, ya probé XMMS, Rythmbox, Audacious, XMMS2, etc. Pero el sonido con Aimp es el mejor (además que la división de carpetas que hace en el playlist es genial). Tengo poca memoria RAM (256 Mb), así que no puedo usar los reproductores más exigentes. (Si alguien tiene una opción mejor o equivalente, libre, bienvenido!)

El script que uso actualmente: > #!/bin/bash
document=`winepath -l "$1"`
exec wine start.exe "$document"

No entiendo mucho de scripts, pero básicamente este lo que hace es "decirle" a wine qué tipos de archivos abrir con dicho programa...

---

### Post by Hei Ku on 2009-08-23
El script lo unico que hace es arrancar wine y de ahí reconoce la asociación del archivo con Aimp. Que pasa si seleccionas varios  archivos al mismo tiempo?

Como alternativa ligera, probaste el VLC?

---

