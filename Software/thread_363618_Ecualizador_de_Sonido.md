---
title: "Ecualizador de Sonido"
date: 2007-02-17
forum: Software
---

### Post by matog on 2007-02-17
Alguien sabe de algun ecualizador de sonido para Ubuntu? Creo que solo el XMMS tiene un ecualizador, y los demás reproductores que estuve tocando (Exaile, Listen)....ni señales de tener uno. 
Y la verdad, el sonido sale mejor por Windows....entonces estoy buscando uno que al menos ecualice todo lo que sale de la compu....algo es algo.

Saludos!

---

### Post by felipelerena on 2007-02-17
gxine es una buena opcion. igual lo que tenes que hacer para equalizar "todo" el sonido que sale tenes que tocar la configuracion de gstreamer....
¿donde esta eso? recien lo busque y no lo encontre pero una vez lo vi, lo deje ecualizado y nunc amas lo toque.

Y en mi Ubuntu todo suena mucho mas lindo y mas libre que en Windows.

---

### Post by jpmorelli on 2007-02-19
Si lo queres hacer PRO te digo que existe algo que se llama jack, si conoces algo sobre audio te explico que es como una patchera para unir diferentes programas que utilizan el sonido y se les puede agregar efectos, etc. Por lo que ví no debe ser fácil de configurar pero bueno, ya sabemos que a los Linuxeros nos encanta eso de pelearla hasta que salga.
Un proyecto que me sorprendió muchísimo cuando me enteré fue Ubuntustudio [http://ubuntustudio.org/]("http://ubuntustudio.org/"), simplemente para los que nos gusta hacer música algo GRANDIOSO ! :guitar:
Ya que estamos tambien te cuento que Amarok ( para mi el mejor reproductor de audio que hay para Linux, aunque cada vez lo hacen más pesado, grrr ) trae su ecualizador y varios presets que suenan muy bien ! Suerte.

---

### Post by matog on 2007-02-20
> **jmorelli said:**
> Si lo queres hacer PRO te digo que existe algo que se llama jack, si conoces algo sobre audio te explico que es como una patchera para unir diferentes programas que utilizan el sonido y se les puede agregar efectos, etc. Por lo que ví no debe ser fácil de configurar pero bueno, ya sabemos que a los Linuxeros nos encanta eso de pelearla hasta que salga.
Un proyecto que me sorprendió muchísimo cuando me enteré fue Ubuntustudio [http://ubuntustudio.org/]("http://ubuntustudio.org/"), simplemente para los que nos gusta hacer música algo GRANDIOSO ! :guitar:
Ya que estamos tambien te cuento que Amarok ( para mi el mejor reproductor de audio que hay para Linux, aunque cada vez lo hacen más pesado, grrr ) trae su ecualizador y varios presets que suenan muy bien ! Suerte.

No, nada profesional. Solamente mejorar el sonido de mis mp3...
Si, sabía lo de Amarok...pero uso Gnome y tengo Exaile como reproductor...aunque por ahi instale Amarok para ver si puede existir diferencia en el sonido con el ecualizador...

Gracias!

---

### Post by BlackHero on 2007-02-21
mira el bpm o beep media player es lo mejor para mi lo mas liviano y adivina para tu gusto si trae ecualizador :D beep media player vendria a ser algo asi como el winamp 3.0 =)

---

### Post by jorgeriv on 2010-07-13
Hola, te recomiendo utilices pulseaudio equalizer

puedes encontrar el paquete .deb en aquí: [http://ubuntuguide.net/wp-content/uploads/2009/12/pulseaudio-equalizer_2.4_all.deb](http://ubuntuguide.net/wp-content/uploads/2009/12/pulseaudio-equalizer_2.4_all.deb)

Es un buen ecualizador para GNU/Linux, te recomiendo bajes la preamplificación a 1.0x (por defecto viene en 1.5x) para que no obtengas un sonido muy saturado. Después ecualiza el sonido a tu gusto o elije alguna preset. 

Nota: requiere pulseaudio actualizado ver. 0.9.21
lo puedes actualizar desde la consola: xxx:~$ sudo apt-get install pulseaudio
(probablemente ya lo tengas instalado)

---

### Post by emiliano_raso on 2010-07-16
> **matog said:**
> No, nada profesional. Solamente mejorar el sonido de mis mp3...
Si, sabía lo de Amarok...pero uso Gnome y tengo Exaile como reproductor...aunque por ahi instale Amarok para ver si puede existir diferencia en el sonido con el ecualizador...

Gracias!

Para instalar Amarok te recomiendo instalar la version vieja (Amarok 1.4) que está a mi gusto mejor que la nueva version (Amarok 2).

Acá en mi blog puse la info de como instalarlo en Ubuntu 10.04
[http://tipslinuxeros.blogspot.com/2010/06/instalar-amarok-14-en-ubuntu-1004-lucid.html](http://tipslinuxeros.blogspot.com/2010/06/instalar-amarok-14-en-ubuntu-1004-lucid.html)

---

### Post by Mister X on 2010-07-16
> **jorgeriv said:**
> Hola, te recomiendo utilices pulseaudio equalizer

puedes encontrar el paquete .deb en aquí: [http://ubuntuguide.net/wp-content/uploads/2009/12/pulseaudio-equalizer_2.4_all.deb](http://ubuntuguide.net/wp-content/uploads/2009/12/pulseaudio-equalizer_2.4_all.deb)

Es un buen ecualizador para GNU/Linux, te recomiendo bajes la preamplificación a 1.0x (por defecto viene en 1.5x) para que no obtengas un sonido muy saturado. Después ecualiza el sonido a tu gusto o elije alguna preset. 

Nota: requiere pulseaudio actualizado ver. 0.9.21
lo puedes actualizar desde la consola: xxx:~$ sudo apt-get install pulseaudio
(probablemente ya lo tengas instalado)


Gracias, lo instalé y parece muy bueno.
Siempre busqué algo así, simple y sumamente util para los que queremos personalizar el sonido que escuchamos.

---

