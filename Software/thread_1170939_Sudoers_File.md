---
title: "Sudoers File"
date: 2009-05-26
forum: Software
---

### Post by DrKenobi on 2009-05-26
Hola. Recien termino de instalar con un cd alternativo un ubuntu para power pc de linea de comando. Todo bien hasta que decido instalar algun paquete con el SUDO.

Cuando escribo "sudo aptitude install cualquiercosa" me dice que mi usuario no esta en el sudoers file.

Como arreglo esto? Yo en ningun momento cree un usuario root, asi que con el unico que tengo no puedo instalar nada.

Gracias

---

### Post by staar on 2009-05-26
tu usuario no es sudoer? entonces estas al horno, seguramente algún error en la instalación, no creo que el sistema sea usable...

primero probá si podes hacer un su a root ```
su root
``` y, si podés, con ```
visudo
``` podés editar el sudoers, OJO ese archivo se tiene que editar con ese comando, nada de nano, y acordate que es vi, que es un editor medio jodido de usar...

sino, creo que lo más rápido va a ser que reinstales...

saludos

---

### Post by DrKenobi on 2009-05-26
Intente con

```
su root
```

y nada.

Voy a tener que reinstalarlo nomas.... mañana, hoy ya es tarde

Gracias por lo de **visudo**, es buenos saberlo.

---

### Post by DrKenobi on 2009-05-27
Lo pude solucionar sin reinstalar!!!!!

Explico lo que hice. Lo primero fue loguearme como root. Entonces entre en "Recovery Mode".

> Al iniciarse el pc aparece el menú del Grub, en el que aparecen al menos tres opciones ( o mas si tenemos Windows, o mas de un kernel de Linux ): 1- Inicio Normal del Sistema 2- inicio en &#8220;Recovery Mode&#8221;  3- Memtest86+. Al iniciarse el pc en Recovery Mode, éste se inicia, en principio en modo consola con permisos de root; hay que esperar a que dejen de aparecer una serie de lineas y que se quede fijo en una línea que acaba con: root@guadav5:&#732;# ( suponiendo que guadav5 sea el nombre que hayamos puesto a nuestro pc cuando instalamos el sistema)

*Fuente:* [http://hatteras.wordpress.com/2009/04/11/iniciar-el-sistema-en-recovery-mode/]("http://hatteras.wordpress.com/2009/04/11/iniciar-el-sistema-en-recovery-mode/")

En realidad, como yo estoy usando una iMac con PowerPC lo que hice fue en la segunda parte del yaboot presionar TAB, luego escribir

```
Linux single
```

y luego presionar enter. *PD:* si estas con un PowerPC y despues de hacer esto se te apaga el iMac, ademas tenes que escribir **nosplash**. Entonces quedaria asi:

```
Linux nosplash single
```

*Atencion:* fijate que **Linux** esta con la **L** en mayuscula!!

*Fuente:* [URL="http://ubuntuforums.org/showthread.php?t=373141"]http://ubuntuforums.org/showthread.php?t=373141
[/URL]
------------

Cuando se termina de cargar lo que tenes que hacer es elegir la opcion

> root - Drop to root shell prompt

Luego escribir

```
visudo
```

agregar esta linea al final del archivo

```
*tu_usuario* ALL=(ALL) ALL
```

*PD:* ***tu_usuario*** es algo generico, ¿se entiende no?

y luego reiniciar usando

```
shutdown -r now
```

Ahora ya deberias poder usar el **sudo**.

*Fuente:* [http://ubuntuforums.org/showthread.php?t=1145828&highlight=sudoers]("http://http://ubuntuforums.org/showthread.php?t=1145828&highlight=sudoers")

Lo unico que te puede pasar es que cuando vuelvas a arrancar el iMac se te vuelva a apagar despues de la segunda parte del yaboot. Aqui simplemente tenes que poner **Linux nosplah**. Por algun lado lei que esto se puede poner para que lo haga solo, pero por el momento no lo se.

---

### Post by staar on 2009-05-27
buenisimo! me alegro, aunque me mataste con eso de yaboot, que es? un bootloader como GRUB pero para PowerPC?

saludos

---

### Post by DrKenobi on 2009-05-27
> **staar said:**
> buenisimo! me alegro, aunque me mataste con eso de yaboot, que es? un bootloader como GRUB pero para PowerPC?

saludos

Asi es, es un bootloader para PPC

---

