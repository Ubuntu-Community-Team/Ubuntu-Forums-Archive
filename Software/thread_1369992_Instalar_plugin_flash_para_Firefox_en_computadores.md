---
title: "Instalar plugin flash para Firefox en computadores de 64 bits"
date: 2010-01-01
forum: Software
---

### Post by nechus on 2010-01-01
Hola a todos. A continuación dejo instrucciones para instalar Flash en sistemas de 64 bits.

Esto soluciona una serie de comportamientos extraños de Firefox, como que los videos se ven bien en Youtube pero no en otros sitios, o no se puede avanzar o retroceder un video que se está viendo en línea, o pinchas play pero no pasa nada, etc.

La razón es que, extrañamente, el plugin de flash incorporado en Ubuntu de 64 bits es el que corresponde a 32 bits. Por eso no funciona bien.

Primero hay que eliminar todo rastro de flash o gnash mediante Synaptic, llámese flashplugin-nonfree, gnash, mozilla-plugin-gnash, etc.

Después de eso cierras Synaptic e ingresas esta línea en la terminal:
sudo apt-get clean && sudo apt-get autoremove
Con eso tu sistema quedó limpiecito.

Ahora bajas [este]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") archivo, que es el plugin flash de 64 bits.

Buscas dónde descargaste el archivo, le haces clic derecho > extraer aquí.

El archivo resultante (libflashplayer.so) lo pones en tu carpeta personal.

Ingresas esta línea en la terminal:
sudo cp /home/TUNOMBREDEUSUARIO/libflashplayer.so /usr/lib64/mozilla/plugins
¡¡¡Te aseguras de cambiar TUNOMBREDEUSUARIO por el nombre de tu cuenta, por supuesto!!!

Reinicia Firefox si lo tenías abierto (sugiero reiniciar el computador para mayor seguridad), y VOILÀ!!!


:KSTutorial traducido, copiado, pegado y adaptado para el usuario chileno promedio desde [http://ubuntuforums.org/showthread.php?t=1356745&highlight=sudo+apt-get+clean](http://ubuntuforums.org/showthread.php?t=1356745&highlight=sudo+apt-get+clean)

---

### Post by CdK1 on 2010-01-01
No es necesario bajar nada -a mi humilde parecer- el deb de los repositorios de flash, funciona sin ningún problema en 64 bits...

---

### Post by nechus on 2010-01-01
Me alegro por ti.

---

### Post by de-troit on 2010-01-05
Muchas gracias por el post, me solucionó el problema que me venía inflando las pelotas hace mucho :P

Saludos Nechus!

---

### Post by moreback on 2010-01-05
Interesante, yo también tengo problemas con algunos flash, voy a intentar esto pero lo voy a hacer en la carpeta de usuario para no estropear mi sistema.

Saludos cordiales.

PD: al final tuve que hacer lo que dijiste, el flash instalado por Synaptic no deja que se detecte el que instalo como usuario.

---

### Post by nechus on 2010-01-05
¡¡Bien!! ¡Qué bueno que el tutorial les sirve!  Este pingüino hizo algo útil.

---

### Post by asterix77 on 2010-01-06
Bueno, ayer bajé una animación en flash, y la quise reproducir con firefox. De partida no me la reprodujo de corrido, corría a intervalos; y para continuar la animación tenía que dar click derecho del mouse (sobre la animación), y dar un click en la opción de reproducción. 

Además en algunas páginas con animaciones flash embebidas, igual tenía algunos problemas, no me agarraban algunos botones, en fin; espero que con esto se arreglen estos inconvenientes.

Se agradece.

---

