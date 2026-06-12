---
title: "Resolución de pantalla SPLASH"
date: 2009-06-24
forum: Software
---

### Post by Andyvec on 2009-06-24
Hola  todos.

Necesito cambiar la resolución de pantalla del SPLASH, no es nada importante, pero cada vez que inicia el sistema mi monitor hace aparecer un cartel indicando que no esta funcionando en el modo recomendado de 1360x768 @ 60Hz.

Encontré uina excelente guía para cambiarlo en esta dirección:
[http://www.guia-ubuntu.org/index.php?title=Cambiar_resoluci%C3%B3n_del_splash_de_inicio_del_sistema]("http://www.guia-ubuntu.org/index.php?title=Cambiar_resoluci%C3%B3n_del_splash_de_inicio_del_sistema")

Pero la guía no indica cuál es el número que corresponde a una resolución de 1360x768 @ 60hz.

Desde ya les agradecería mucho que me lo indiquen :KS, seguramente estos números sean de un estándar que ignoro.

---

### Post by pablo.s on 2009-06-24
Un consejito chiquito:
Es mucho mas facil
deshabilitar el OSD
del monitor que meter
mano en la configuracion
de Usplash y despues
arrepentirse.
Saludos.

---

### Post by staar on 2009-06-24
pablo no es nada muy complicado, solo hay que colocar la opción del framebuffer adecuado en la línea del kernel...

mirá, la mejor forma de saber que modos tenés disponibles (dependen de tu placa de video y del driver en uso) es corriendo ```
sudo hwinfo --framebuffer | grep Mode
``` en una Terminal (te sale un número tipo 0x031b, tenés que ponerlo así), aunque puede que no funcione, o puede que la usplash no se vea, lo mejor que podés hacer si no anda, es usar el valor para 1024 x 768, que por lo menos tiene la misma altura...

saludos

---

### Post by Andyvec on 2009-06-24
> **staar said:**
> mirá, la mejor forma de saber que modos tenés disponibles (dependen de tu placa de video y del driver en uso) es corriendo ```
sudo hwinfo --framebuffer | grep Mode
``` en una Terminal (te sale un número tipo 0x031b, tenés que ponerlo así)

¿Está bien escrito? Pues me dice: ```
sudo: hwinfo: command not found
```

pd: No es posible deshabilitar el OSD del monitor, se enciende automáticamente al detectar la resolución "no conveniente".

---

### Post by staar on 2009-06-24
hwinfo creo que no viene instalado por defecto, instalalo con ```
sudo aptitude install hwinfo
```

saludos

---

### Post by Andyvec on 2009-06-24
Gracias  todos, pero el resultado que me da es el siguiente:

```
  Model: "NVidia NV11 Board"
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits

```

Donde no figura mi resolución actual que es 1360x768 widescreen.

Lo que yo necesito es un número diferente, es el numero que se agrega modificando el archivo "sudo gedit /boot/grub/menu.lst" como explica el tutorial que cite al principio. Por ejemplo se que 790 equivale a 1024x768 con 32k de colores, pero yo necesito el código de tres números para 1024x768 @ 32k.

---

### Post by guillermolisi on 2009-06-24
> **Andyvec said:**
> Gracias  todos, pero el resultado que me da es el siguiente:

```
  Model: "NVidia NV11 Board"
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits

```

Donde no figura mi resolución actual que es 1360x768 widescreen.

Lo que yo necesito es un número diferente, es el numero que se agrega modificando el archivo "sudo gedit /boot/grub/menu.lst" como explica el tutorial que cite al principio. Por ejemplo se que 790 equivale a 1024x768 con 32k de colores, pero yo necesito el código de tres números para 1024x768 @ 32k.
La notacion de 32k para la profundidad de colores es un invento de Windows. La notacion correcta para lo que seria True Color, la maxima profundidad, es 24 bits (no k).

Por el listado generado con hwinfo, esa placa de video llega como maximo a 1024*768@24 bits.

Podes resignar profunidad de colores y llevarla a 1600x1200@16 bits para que aun sea aceptable cromaticamente hablando.

---

### Post by staar on 2009-06-24
guillermo, aclarar que siempre hablando de framebuffer...

andy, en el grub podés ponerlo de las dos formas, con un número de tres cifras o con esos 0x033, si tu placa no soporta esa resolución en framebuffer, lo siento, desconozco si hay forma de obligarla...

saludos

---

### Post by guillermolisi on 2009-06-24
> **staar said:**
> guillermo, aclarar que siempre hablando de framebuffer...

andy, en el grub podés ponerlo de las dos formas, con un número de tres cifras o con esos 0x033, si tu placa no soporta esa resolución en framebuffer, lo siento, desconozco si hay forma de obligarla...

saludos
Si, perdon. Gracias por la aclaracion.

---

### Post by Andyvec on 2009-06-25
Entiendo, pero mi placa si funciona con esa resolución porque es la que estoy usando ahora mismo, además anteriormente el splash estaba a la resolución correcta, pero por un error borré parte del grub y tuve que reemplazarlo por un archivo estándar que esta a 1024x768 y no a 1360x768 que es la resolución óptima de mi monitor.

Si supiera cuál es el código para 1360x768 en @ 32 colores, podría probar, pero el hwinfo por alguna razón no me da el código para esa resolución.

---

### Post by guillermolisi on 2009-06-25
> **Andyvec said:**
> Entiendo, pero mi placa si funciona con esa resolución porque es la que estoy usando ahora mismo, además anteriormente el splash estaba a la resolución correcta, pero por un error borré parte del grub y tuve que reemplazarlo por un archivo estándar que esta a 1024x768 y no a 1360x768 que es la resolución óptima de mi monitor.

Si supiera cuál es el código para 1360x768 en @ 32 colores, podría probar, pero el hwinfo por alguna razón no me da el código para esa resolución.
Hay algo que no termino de entender. Queres que tu monitor funcione a esa resolucion y profundidad de colores, con Ubuntu, porque ahora no podes lograr ese objetivo. Luego decis que ahora esta en esa resolucion ... me perdi algo en el camino ...

O lo que te falta es solamente que la splash screen se vea en esa resolucion y colores ?

---

### Post by staar on 2009-06-25
yo entendí que no tiene problemas en el escritorio, que el problema es con el usplash...

las resoluciones en framebuffer no son las mismas que en el escritorio, ya que se usan antes de que el driver esté cargado, por eso digo que depende de la placa...

el problema es que ese código no sigue un estándar (hay uno, que se respeta poco) en la mayoria de los casos, depende del ensamblador y el modelo de la placa de video, sobre todo con resoluciones wide, por ejemplo el modo 0x0368 puede ser 1360x768 o 1280x768 en placas intel, 1680x1050 en placas nvidia, etc...

el hwinfo te muestra las resoluciones que el driver framebuffer de tu placa es capaz de soportar, pero si decís que antes estaba bien seteado, la verdad que no sé, hay otra forma de saber que resoluciones soporta, que es poniendo vga=ask, pero en la línea del kernel en el menu.lst, así ```
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=c7bca061-60b2-4fe2-a8aa-19ade6201585 ro quiet **vga=ask** splash
``` (ese es mi menu.lst, el tuyo es **diferente**, NO copies y pegues)

otra cosa, 32 bits de colores es un invento de windos, son 24 bits de colores (3 canales de 8 bits) y 8 bits del canal alpha, que en framebuffer menos sentido aún tiene contar...

saludos

---

