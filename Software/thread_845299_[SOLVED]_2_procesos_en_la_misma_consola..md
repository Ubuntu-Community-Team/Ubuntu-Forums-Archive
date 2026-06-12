---
title: "[SOLVED] 2 procesos en la misma consola."
date: 2008-06-30
forum: Software
---

### Post by Mauro22 on 2008-06-30
Buena!!


Tengo un problemilla que no puedo resolver.

Tengo un script en bash en el cual necesito hacer dos cosas:

1) Desactivar compiz
2) Lanzar el juego

El problema que el comando metacity --replace (sera este??) deja la consola "abierta" es decir, no se se puede hacer otra cosa. Por lo tanto el juego nunca se abre.

Ahora, no se si es por esto o por otra cosa :(

Probe:

metacity--replace&

metacity --replace &

nohup metacity --replace&

nohup metacity --replace &

Me baje un programa que se llama compiz-switch. Tampoco


Lo que logro es sacar compiz, pero no poder ejecutar nada mas.



Existe algo?
Alguna forma de mandar el comando 2 a otra consola?



Gracias de antemano!

---

### Post by Mister X on 2008-06-30
El siguiente script te deberia andar, El ampersand al final de un comando lo hace ejecutar en background, por lo tanto pasa inmediatamente al siguiente comando. Si tenes el problema que cuando se ejecuta el juego todavia no alcanzo a deshabilitarse el compiz, podes agregarle un retardo (sleep) antes de ejecutar el comando del juego.

```
!/bin/bash

metacity --replace &
nombre_del_juego

```

---

### Post by faktorqm on 2008-07-01
A mi se me ocurrio basicamente es que llames a otra consola y le pases el comando por parametros, o sea, esto funciona, ahora no se si es lo mas "sano" tecnicamente hablando. el comando es el siguiente:

```
xterm -e metacity --replace
```

entonces eso te abre otra consola y te ejecuta ese comando. Fijate que onda. Salu2!

---

### Post by Mauro22 on 2008-07-01
Lo voy a probar y te cuento.

Ni idea de ese comando :o

---

### Post by faktorqm on 2008-07-01
no es nada de otro mundo, utilice el concepto de, por ejemplo, cuando vos pones "firefox http://www.google.com.ar/" y el tipo te abre esa pagina. Entonces si a xterm le decia lo mismo quiza funcionaba... solo que no ocurrio y lei el help y decia que para hacer habia que poner -e y listo el pollo. Es una cuestion de conceptos mas que nada. SAlu2!

---

### Post by Mauro22 on 2008-07-01
Estoy mas cerca...


El comando ese anda genial, pero para seguir ejecutando el script tengo que apretar control + c

Tengo que ver como simular esa combinacion para que haga todo automatico!

:guitar:

---

### Post by Mauro22 on 2008-07-06
Solucionado


En vez de xterm -e, hay que usar gnome-terminal -e 


Y ahi si, ejecuta varios...


En realidad abre consolas independientes entre si.


:guitar:

---

