---
title: "No puedo utilizar amarok"
date: 2009-02-01
forum: Software
---

### Post by Mariel on 2009-02-01
Hola! La verdad es que no domino para nada todo lo que esté relacionado con la computación. Pero quiero ir aprendiendo y esta es una manera de empezar.
Hace poco me actualizaron la versión de Ubuntu (igual no me pusieron la más más nueva) y resulta que ahora quiero utilizar Amarok y no puedo. Cuando apreto sobre el iconito me aparece el reloj, pero luego de unos instantes desaparece el reloj y no se me abre ninguna ventana, no se me abre el Amarok. Es como si no le hubiese pedido nada a la compu, como si no hubiese apretado nada. No tengo idea de por qué sucede esto. Alguien tiene alguna respuesta?? Como dije antes, yo no tengo la más mñinima noción.

---

### Post by Hei Ku on 2009-02-01
Abri una terminal y escribi:

amarok

Debería aparece algo, y con suerte un error que nos de una idea de por qué no anda. Copialo aca y seguimos con eso.

---

### Post by Mariel on 2009-02-01
> **Hei Ku said:**
> Abri una terminal y escribi:

amarok

Debería aparece algo, y con suerte un error que nos de una idea de por qué no anda. Copialo aca y seguimos con eso.

Me apareció esto:
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by Hei Ku on 2009-02-01
Los dos primeros errores no tienen importancia. El que importa es el último. Esta buscando una biblioteca que no esta.

Probemos esto:

```

sudo ln -s /usr/lib/xorg/libGL.so.1 /usr/lib/libGL.so.1

```

---

### Post by Mariel on 2009-02-01
Puse eso que me dijiste (sudo ln -s /usr/lib/xorg/libGL.so.1 /usr/lib/libGL.so.1) en Terminal (está bien o hice cualquiera?). Después apreté "Enter" y entonces me pidió mi contraseña. Y la escribí. Ahora?

---

### Post by Hei Ku on 2009-02-01
Proba de iniciar Amarok de vuelta, a ver qué pasa.

---

### Post by Mariel on 2009-02-01
Ahí probé, pero no pasa nada...

---

### Post by Hei Ku on 2009-02-01
Si pones Amarok en la terminal te sigue tirando el mismo error?

Que te sale si pones este comando en la terminal?

locate libGL.so.1

---

### Post by Mariel on 2009-02-01
Sí, si pongo Amarok en la terminal me sale el mismo error. Y si pongo el comando queme dijiste me sale esto:
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib32/fglrx/libGL.so.1.2.xlibmesa
/usr/lib32/fglrx/libGL.so.1.xlibmesa

---

### Post by Hei Ku on 2009-02-01
Pone esto en la terminal.

sudo ln -s /usr/lib/fglrx/libGL.so.1.xlibmesa /usr/lib/libGL.so.1

Si te tira algun error, decime. Si no, volve a probar el Amarok.

---

### Post by Mariel on 2009-02-01
Justo te había mandado un mensaje.
Puse lo que me dijiste, me pidió la contraseña y después apareció esto: ln: creando el enlace simbólico `/usr/lib/libGL.so.1' a `/usr/lib/fglrx/libGL.so.1.xlibmesa': El fichero ya existe

---

### Post by Hei Ku on 2009-02-01
Si, me parecia que podia dar error.

Pone esto en la terminal:

sudo rm /usr/lib/libGL.so.1
sudo ln -s /usr/lib/fglrx/libGL.so.1.xlibmesa /usr/lib/libGL.so.1

---

### Post by Mariel on 2009-02-01
Ahí lo puse.
Y probé de nuevo pero no, no se abre el Amarok.

---

### Post by Mariel on 2009-02-01
Mil gracias, la seguimos en otro momento.

---

### Post by Hei Ku on 2009-02-02
El bug es este: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369)

Pero no sé como solucionarlo en tu sistema. Me parece que te falta algún paquete de OpenGL.

---

### Post by Wartin on 2009-02-02
> **Hei Ku said:**
> El bug es este: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369)

Pero no sé como solucionarlo en tu sistema. Me parece que te falta algún paquete de OpenGL.

Sí, efectivamente. Yo había estado intententando instalar los drivers de su placa ATI (una un poco rara, on board) y algo falló...

Finalmente lo solucionamos instalando libgl1-mesa-swx11, lo que desinstaló libgl1-mesa-glx y kubuntu-desktop (que desinstaló algunos paquetes que no me importan mucho). Igual sigo usando el driver vesa, hasta que actualice a Hardy y su driver venga en un paquete...

Pero bueno, ya tiene un libGL.so.1, que es lo que necesitaba Amarok (me pregunto para qué...).

Saludos y gracias!

---

### Post by Mariel on 2009-02-02
Gracias Wartin!!!

---

