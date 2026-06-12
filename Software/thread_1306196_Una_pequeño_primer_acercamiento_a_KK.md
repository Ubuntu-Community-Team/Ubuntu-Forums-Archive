---
title: "Una pequeño primer acercamiento a KK"
date: 2009-10-30
forum: Software
---

### Post by anarko on 2009-10-30
Y un gran problema, va varios, les cuento mi estadia en KK que por como se vienen desarrollando las cosas estoy por volver a 904.
Arrancamos bien, baje la ISO hice mi USB booteable, reinicie y arranco de maravilla. Megusta como se ve el bootsplash y todo. Anes de instalar estube jugando un poquito como es necesario. Aqui arrancaron los problemas, quise configurar en ADSL y como era de esperarse el gestor de redes de Gnome no ando ni un poquito, lo que me sorprendio es tampoco ando el pppoe ( no me hechen la culpa a mi, hasta antes de reiniciar estaba conectado con 904 ), el gestor de redes de gnome pareceia no saber donde guardaba la contraseña de mi ADSL la puse como 2000 veces y despues volvia a entrar y se habia ido, dije bla, instalo y le doy con el pppoeconf como dios manda.

La instalacion una maravilla las diapositivas re linda, un monton de cosas hermosas, me llamo la atencion instalao en 3 minutos, tarde mas en contestar las preguntas de mi nombre y particionar el disco que en instalar, a lo que dije EXELENTE esto VUELA.

Terminada la instalacion reinicie, lindo el grub2 ( bueno 1.999999999999 :p ), arranco con el bonito bootplahs, y ahi si ahi empezeron los problemas : 

1) el gestor de redes obviemente jamas funciono, pero como viene pasando desde 6.06 dije, culquiera se sigue equivocando, pppoeconf y a la cancha, esa parte me salio bien si no fuera porque el pppoeconf olvido hacer un par de enteres en el interfaces y habia quedado todo amonotonado y lo tube que solucionar a mano.

2) bajo el mc ( midnaith commander ), yo laburo mucho en consola y me gusta el mc para hacer las cosas, en el mc no habia forma de que guarde las preferencias, dije quepaso, voy y miro en mi home .mc con dueño root grupo root permisos solo para root, como llego eso ahi?

3) se colgo, pero se colgo mal, se frizo la pc entera, cosa que JAMAS me ha pasado, previo boton de reset arranco de nuevo

4) configuro mi programa para ver la tele preferido ( tvtime ) y O POR DIOS esto tampoco graba las config, obviamente tube que arreglar los permisos de .tvtime en mi home.... esto se pone denso dije.

5) No se escucha, dije, seguro es el volumen del line-in que esta bajo, vamos a subirlo, HAY MAMA PULPA NO HAY MIXER!!!!!!!!!!! alguien vio el mixer? Fujitivo mixer en ubuntu 9.10 recompensare.....
Solucion aptitude install alsa-mixer

Bueno estos fueron solo las pequeñas cosas que me pasaron, en los 10 minutos que lo probe despues de todo eso absolutmente frustrado y sin consuelo por haber borrado el 9.04 me fui a dormir invadido por una enorme tristeza, avanzaron en lo visual y retrocedieron 10 años en lo practico. 

Ubuntu 9.10 arranco MAL para mi
Saludos.

---

### Post by fmsismo on 2009-10-30
Incorpora a la lista de mejoras en la 9.10 que el modem 3g hawawei 220 no lo ve como modem 3g.

Hice un upgrade de 9.04 a 9.10.  Un dolor de cabeza.  Busco por información y parece ser que es un bug detectado antes de que salga la versión oficial pero no había tiempo para cambiarlo :-S

---

### Post by aledruetta on 2009-10-30
Me llama la atención el hecho de que estoy teniendo más dificultades con la versión final de las que tuve con la Beta y la RC. 

Por ejemplo, quise crear un Disco de Inicio USB en mi pendrive y no hubo caso de que me lo acepte. Eso lo hice 40 veces en las versiones de prueba de KK.

Con Firefox también tuve dificultades para que me tome algunos complementos (que ya los había probado mil veces en las versiones de prueba)

Algunos bloqueos extraños en el Ubuntu Software Center que hasta ahora no habían sucedido.

Y aclaro que estoy hablando de una instalación limpia, porque del upgrade que hice en otra máquina, mejor ni hablar...

Esperemos que en unos días se empiecen a solucionar los problemas.

---

### Post by oktubrer on 2009-10-30
> **anarko said:**
> 
2) bajo el mc ( midnaith commander ), yo laburo mucho en consola y me gusta el mc para hacer las cosas, en el mc no habia forma de que guarde las preferencias, dije quepaso, voy y miro en mi home .mc con dueño root grupo root permisos solo para root, como llego eso ahi?

3) se colgo, pero se colgo mal, se frizo la pc entera, cosa que JAMAS me ha pasado, previo boton de reset arranco de nuevo

4) configuro mi programa para ver la tele preferido ( tvtime ) y O POR DIOS esto tampoco graba las config, obviamente tube que arreglar los permisos de .tvtime en mi home.... esto se pone denso dije.


Que raro el tema de los permisos, muchos problemas se pueden deber a eso, por las dudas te recomendaria cambiar recursivamente usuario y grupo de tu home, para quitar todos los owner root, y reiniciar sesión.

---

### Post by anarko on 2009-10-31
Agregamos una mas. 2 dias despues : 
```

anarko@anarka:~$ firefox
Error en el bus
anarko@anarka:~$ firefox -g
/usr/bin/gdb /usr/lib/firefox-3.5.4/firefox -x /tmp/mozargs.ePNSh3
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Leyendo símbolos desde /usr/lib/firefox-3.5.4/firefox...(no debugging symbols found)...hecho.
(gdb) run
Starting program: /usr/lib/firefox-3.5.4/firefox 
[Thread debugging using libthread_db enabled]

Program received signal SIGBUS, Bus error.
0x00007ffff7df6918 in ?? () from /lib64/ld-linux-x86-64.so.2
(gdb)

```

Por suerte tengo una maquina con 904 de la que pude copiarme el repositorio chrome.

---

