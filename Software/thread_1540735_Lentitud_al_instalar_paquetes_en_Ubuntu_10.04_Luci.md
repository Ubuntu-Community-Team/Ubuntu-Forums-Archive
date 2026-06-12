---
title: "Lentitud al instalar paquetes en Ubuntu 10.04 Lucid Lynx"
date: 2010-07-28
forum: Software
---

### Post by Spity on 2010-07-28
Hola! 
Hace poco migré una PC a Ubuntu 10.04 Lucid Lynx (Vengo desde Debian) y la primer cosa "rara" que noto es que al momento de instalar paquetes (y no me refiero a descargar de internet) se demora casi el doble de lo que debería tardar.  Sea por medio de Synaptic o consola.
Descarto que sean problemas de rendimiento de la pc ya que en Debian e incluso en versiones anteriores de Ubuntu no tenía este "problema". Agradecería alguna ayuda o comentario al respecto.
Gracias!

---

### Post by guillermolisi on 2010-07-28
Cuanto es el doble de lo que deberia tardar ?

Synaptic o apt-get usan el mismo mecanismo para bajar e instalar paquetes (dpkg).

No tendras algun proceso consumiendo recursos en exceso y eso hace que vaya mas lento ? (suponiendo que esta lentitud se verifique).

No todos los paquetes demoran lo mismo en instalarse (tampoco en bajarlos de la Net).

---

### Post by Spity on 2010-07-28
Hola Guillermo, el doble o más! 
Cualquier paquete sean uno o dos, actualizaciones o cualquier cosa que instale tarda mucho. Puse el "doble" pero en realidad hay veces que tarda mucho mas... 
Por ejemplo: Se queda en "desempaquetando x paquete" y ahí queda 1, 2 o 3 minutos sin hacer nada. Y de repente comienza. Y así con cada paquete. La cosa se hace "lerda" cuando instalo varios paquetes, que antes, en otra versión de Ubuntu, como por ejemplo Karmic no tenía problema. 
A tu pregunta, no, procesos que consuman muchos recursos no. Ni siquiera uso compiz. :)
No es que sea algo que me complique mucho, pero me llamó la atención y quería consultarlo.

---

### Post by guillermolisi on 2010-07-28
> **Spity said:**
> Hola Guillermo, el doble o más! 
Cualquier paquete sean uno o dos, actualizaciones o cualquier cosa que instale tarda mucho. Puse el "doble" pero en realidad hay veces que tarda mucho mas... 
Por ejemplo: Se queda en "desempaquetando x paquete" y ahí queda 1, 2 o 3 minutos sin hacer nada. Y de repente comienza. Y así con cada paquete. La cosa se hace "lerda" cuando instalo varios paquetes, que antes, en otra versión de Ubuntu, como por ejemplo Karmic no tenía problema. 
A tu pregunta, no, procesos que consuman muchos recursos no. Ni siquiera uso compiz. :)
No es que sea algo que me complique mucho, pero me llamó la atención y quería consultarlo.
Entiendo.

Notas algo relevante cuando actualizas via apt-get o Synaptic exhibiendo su consola ?
El proceso se detiene en algun punto en particular siempre ?
Se detiene en un solo momento o en mas de uno ? Tenes observado algun patron ?

---

### Post by atari130xe on 2010-07-28
En mi caso no es para tanto pero sí debo reconocer que algún cambio y actualización de apt-get o Gdebi hubo desde hace un par de versiones, lo digo porque ahora que leí este post me apareció en la mente este tema, antes (por ahí estoy equivocado) era instalar algún .deb (desempaquetar e instalar y listo) ahora como que se queda verificando o algo así hasta la 8.04 noté que era más rápido instalar paquetes luego de eso no. (por ahí estoy equivocado y es solo una percepción)

---

### Post by Spity on 2010-07-28
Queda congelado en distintas etapas, pero siempre leo "Desempaquetando..." como la que más tarda. Igualmente todo el proceso de instalación de cualquier paquete es sumamente lento.
Por ejemplo, el otro día hice una instalación limpia y luego de descargar las actualizaciones, se demoró casi 30 minutos en instalarlas.
Acá pude capturar donde es que se "tilda" unos minutos, pero repito, es lento en todo el proceso de instalación. 
[[IMG]http://www.imageurlhost.com/images/n96tigsqzdflg3rolgzc_thumb.png[/IMG]](http://www.imageurlhost.com/viewer.php?file=n96tigsqzdflg3rolgzc.png)

Mi PC:
. Disco: SATA II
. AMD Athlon 64 X2 Dual Core 3800+
. RAM: 4 GB DDR2
. NVIDIA Geforce 9400 GT

---

### Post by alfplayer on 2010-07-28
[http://packages.ubuntu.com/lucid/lilypond-doc](http://packages.ubuntu.com/lucid/lilypond-doc)
[SIZE=2]
[/SIZE][SIZE=2]Ese paquete es de 140 MB. Es normal que tarde.
[/SIZE][SIZE=2][/SIZE]

---

### Post by Spity on 2010-07-28
Fue tan solo un ejemplo, temía que esa captura generara confusión, fue al tum tum. 
Ya lo escribí antes, pasa con cualquier paquete, sea de 1mb o hasta de 100mb.

---

### Post by alfplayer on 2010-07-28
No estoy confundido. Es que es raro que en **ese** paso sea más lento, lo que hace es simplemente descomprimir.

---

### Post by guillermolisi on 2010-07-29
Estuve prestando especial atencion a las actualizaciones que hice desde que se abrio este hilo, en maquinas distintas, algunas con Ubuntu 10.04 desktop y otras con server (es decir, distintos requerimientos de paquetes), todas de 32 bits, y no encontre diferencias apreciables como tampoco demoras excesivas en el desempaquetado y aplicacion.

Tampoco recuerdo que las actualizaciones eran mas rapidas cuando utilice Debian Sarge y Etch que sus contemporaneas de Ubuntu. 

No estoy utilizando ninguna maquina con Ubuntu64 bits asi que por ese lado no puedo opinar.

---

