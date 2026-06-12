---
title: "[Pedido] Script para abrir Urban Terror y XBMC sin Compiz"
date: 2008-11-16
forum: Software
---

### Post by majatu on 2008-11-16
Buenas gente, queria preguntar si alguien sabe si se pueden hacer estos scripts y como hacerlos:


Uno que me deshabilite los efectos de Compiz, me abra Urban Terror y cuando cierre el juego, me vuelva a habilitar los efectos de Compiz.

Y otro que haga exactamente lo mismo con compiz pero que me abra el XBMC Media Center y al cerrarlo vuelva compiz.


La idea seria crear un Lanzador para cada script y que se ejecuten, para no tener que deshabilitar y reactivar compiz cada vez que quiera usar los programas.


Un saludo y espero puedan darme una mano :)

---

### Post by Mauro22 on 2008-11-16
yo hacia un script asi:

```

#!/bin/bash
metacity --replace
juego
compiz --replace

```
A veces funcionaba mal, pero casi siempre bien :D


Sino algo asi:

[http://lifehacker.com/342161/toggle-compiz-effects-with-one-click](http://lifehacker.com/342161/toggle-compiz-effects-with-one-click)


Te crea un icono en el panel. Con un clic desctivas compiz y con otro lo volves a activar.

---

### Post by brunovecchi on 2008-11-16
> **Mauro22 said:**
> yo hacia un script asi:

```

#!/bin/bash
metacity --replace
juego
compiz --replace

```


Estoy de acuerdo, aunque quizás convenga agregar '&&' entre los comandos, para que el siguiente se ejecute solo si el primero termina exitosamente:



```

#!/bin/bash
metacity --replace && juego && compiz --replace

```

Dependiendo también de cuan "gracil" sea la salida del juego, quizás convenga agregar un "sleep 5" entre la salida del juego y la reconstitución de compiz, para estar seguros!

---

### Post by majatu on 2008-11-16
Muchas gracias por ambas respuestas, el Compiz-Switch anda barbaro.

Lo que no pude fue hacer andar el script.
Yo al juego no lo tengo instalado ni bajado por ningun repositorio.
Lo ejecuto con un lanzador a /home/miuser/urbanterror/ioUrbanTerror.i386

entonces no se como poner para que me ejecute desde el script al archivo ioUrbanTerror.i386

En el caso del XBMC tampoco me funciona, pongo como comando "xbmc" para que me lo ejecute y al correr el script me deshabilita compiz pero no ejecuta nada :(

Otra cosa que note es que cuando salgo de la terminal porque no se ejecuto mas nada, cuando quiere volver a habilitar Compiz, no lo hace y me desaparecen las barras de las ventanas, se alerda muchísimo la pc y tengo que cerrar la sesión porque no me deja forzar al cierre nada de lo que estoy haciendo :confused:

Muchas gracias!

---

### Post by Mauro22 on 2008-11-16
> **majatu said:**
> 
/home/miuser/urbanterror/ioUrbanTerror.i386


sh /home/miuser/urbanterror/ioUrbanTerror.i386

```

#!/bin/bash
metacity --replace && sh /home/miuser/urbanterror/ioUrbanTerror.i386 && compiz --replace
```

---

### Post by majatu on 2008-11-17
> **Mauro22 said:**
> sh /home/miuser/urbanterror/ioUrbanTerror.i386

```

#!/bin/bash
metacity --replace && sh /home/miuser/urbanterror/ioUrbanTerror.i386 && compiz --replace
```

Buenas, yo de nuevo... vos sabes que no me ejecuta ninguno de los dos programas anteponiendo "sh" tampoco :confused:, osea hace lo mismo que mencione antes, pero no ejecuta mas nada :(

---

