---
title: "Lucid: Problema con menu"
date: 2010-05-05
forum: Software
---

### Post by jorgito on 2010-05-05
Hola a todos, 

Como ya va siendo hora de actualizar desde 8.04, y aunque quiero hacer una intalacion desde cero,  estuve probando el Live CD de 10.04 para ver si todo andaba OK.
La maquina es una Olivetti 820, con un T2060 de 1.6GHz, 2 G de RAM y video Intel 945.
Lo primero que noto es que tarda más de 9 minutos en liberar el escritorio para empezar a trabajar. Son cinco hasta que pone el fondo de pantalla, seis hasta que pone el cursor, y el resto se lo lleva la ventana de instalacion/prueba y cargar el escritorio.
Como referencia, LiveCD de opensuse 11.2 libera el escritorio en menos de tres minutos en la misma maquina.

Lo segundo (que me parece mas problematico) es que en cuanto quiero usar las teclas Fn para subir y bajar el volumen abre la ventanita con el cursor pero titilando a lo loco e inmediatamente se cuelga la barra del menu superior. Puedo matar la ventana titilante, pero el menu sigue colgado.
Además, cuando pasa esto ya no puedo mover o redimensionar ventanas que estuvieran abiertas.
Esto pasa con efectos y sin efectos de escritorio.

Para apagar, tengo que recurrir al viejo y buen Crtl-Alt-Del.

Alguna idea?

Desde ya muchas gracias.
Saludos, 

Jorge

---

### Post by jorgito on 2010-05-07
Algun comentario adicional:

Lo que parece volverse loco cuando uso las teclas Fn para modificar el volumen es el indicator-applet.

Despues de haber usado las teclas Fn, ninguna ventana recupera el foco. Si tengo una terminal abierta ya no puedo escribir más en ella.

Aparentemente no pasa nada con la teclas Fn para el brillo de la pantalla.

Nada más por ahora, 

Saludos

---

### Post by jorgito on 2010-05-17
Hola a todos, 

Bueno, el problema no es solo de Lucid.

Lo que tengo andando es

0.- Ubuntu 8.04, Gnome, 2.6.24-26-generic, Xorg 1.4.0.90

Probe las siguentes distros:
1.- VectorLinux 6.0: KDE, 2.6.27.29, Xorg 1.4.2
Ningun efecto evidente al usar las teclas Fn, pero al menos durante un rato el menu principal enloquece haciendo titilar varias selecciones a la vez. Se "arregla" solo. El teclado no parece colgarse y el mouse lo mismo.

2.- Opensuse 11.2: Gnome, 2.6.31.5-0.1, Xorg 1.6.5
Arranca con efectos de escritorio habilitados.
El indicador enloquece, cuelga el teclado, las ventanas abiertas no pueden moverse o redimensionarse. Cerrando sesion se arregla todo.

3.- Zenwalk Linux 6.0.1: Xfce4, 2.6.28.7, Xorg 1.4.2
Muy similar a 1.-.
Las ventanas abiertas solo se pueden mover unos milimetros, despues se clavan. Las teclas de brillo andan OK. De la terminal abierta solo quedo la barra de titulo.
Parece arreglarse solo. Quizas relacionado con pulsaciones del mouse o con el uso del teclado.
Una vez que se arregla, no repite el efecto, por mas que pulse las teclas de volumen, solo repite despues de cerrar sesion.

4.- Zenwalk Linux 6.0.1: Xfce4, 2.6.28.7, Xorg 1.4.2, pero sin controladores propietarios habilitados (Ignoro si los carga o no. Solo le digo que no los quiero).
Lo mismo que 3.-

5.- Mandriva One 2010: Gnome 2.28, kernel 2.6.31.5, Xorg 1.6.5
Parece mas lento en bootear que los demas. Pide aceptar un licencia (?) Prueba sin efectos de escritorio habilitados.
Abre ventanita con icono de parlante y control de volumen, que no se cierra hasta que le doy Crtl-Backspace. El teclado se cuelga. Las ventanas no se pueden mover, aunque si se pueden cerrar. Los menues no responden. La unica forma dereiniciar es Ctrl-Alt-Del.


6.- Trisquel Pro 2.2.2 i686 Live DVD: Gnome, 2.6.24.26 generic, Xorg 1.4.0.90
No consigo hacer que se reproduzca el problema. O sea: parece andar tan bien como lo hace el Ubuntu 8.04.
Este en principio lo descarto, porque como tengo wifi de intel, soy un subhumano que no merece los beneficios de la penicilina ni la luz eléctrica. (léase: no hay drivers libres para mi placa wifi).

7.- Ubuntu 9.10: Gnome, 2.6.31-14-generic, Xorg 1.6.4
El tiempo de carga es del mismo orden que las demas distros, contra los casi 10 minutos de Lucid.
Las teclas de volumen abren el indicador que queda titilando y que se cierra recien despues de uno o dos minutos. El teclado queda colgado. El menu no responde mas. Para reiniciar solo anda el Crtl-Alt-Del.

8.- Scientific Linux: Gnome, 2.6.18-164.1.el5, X Window version 7.1.1, xorg-x11-server 1.1.1-48.67.el5
Se cuelga la barra de menu, se cuelga el teclado hasta que mato la ventanita con el volumen. Con eso normaliza todo, pero si vuelvo a usar las teclas de volumen se cuelga de nuevo y ya no se recupera. No hay teclado, funciona el doble click sobre el area de mouse, pero no los botones del mouse. Las ventanas no se pueden mover o redimensionar.
Crtl-Alt-Del no funciona, pero si Crtl-Alt-Backspace para salir del escritorio, y luego poder reiniciar o apagar o recargar.

Conclusion: Lo que veo comun entre las dos distros que andan es la version de Xorg: en los dos casos 1.4.0.90.

A ver si con esto se puede hacer algo...
Desde ya muchas gracias.

Jorge

---

### Post by juancarlospaco on 2010-05-17
*Usa la version 10.04 de Ubuntu...*

---

### Post by jorgito on 2010-05-17
Hola 

Gracias, pero es justamente la 10.04 la que dispara este despelote.

Saludos

---

### Post by jorgito on 2010-05-17
Buenas

Parece que el bicho que me pica es: Bug #291612...

---

### Post by jorgito on 2010-05-26
Hola, 

Marco como solved, aunque en realidad es un parche, como para que no moleste.
El problema es que las dos malditas teclas de subir y bajar el volumen generan el evento de tecla apretada, pero NO el de tecla liberada.
Por alguna razón, esto se manejaba bien en 8.04 pero no a partir de 8.10.
El parche es editar combinaciones de teclas para remapear la subida y bajada de volumen a otras que si generen el evento de tecla liberada.

A lo mejor le sirve a alguien mas.

Saludos

---

