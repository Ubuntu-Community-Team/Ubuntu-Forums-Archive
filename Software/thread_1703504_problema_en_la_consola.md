---
title: "problema en la consola"
date: 2011-03-09
forum: Software
---

### Post by tio lucas on 2011-03-09
Hola, tengo un inconveniente con la consola. Tengo Ubuntu 10.04. Lo que pasa es que quiero trabajar en la consola para programar, y el problema que tengo es que la consola es más grande que mi pantalla. No se alcanza a ver todo. 
Probé cambiando el tamaño de la letra reconfigurando console-setup pero el problema sigue. Desactivé el splash sacándolo de los parámetros de la imagen del kernel, pero nada. Le pasé vga=normal pero tampoco.
Lo único que quiero es tener una consola 80x25, no me importa el framebuffer.

---

### Post by juboba on 2011-03-09
¿Qué resolución estás usando? Puedes mover la ventana con ALT-CLICK. Podrías subir un SS.

---

### Post by asterix77 on 2011-03-09
a) Quizás tengas activada la opción de pantalla completa, prueba presionando F11 para salir de ella.

b) Al menos en mi caso, al abrir la terminal (Aplicaciones----->Accesorios ----->Terminal), me aparece en la parte superior un menú, en el cual uno de ellos me dice "Terminal", donde puedes configurar el tamaño, que por defecto es 80x24. 

c) Si lo anterior no resulta, probar con Alt+F2, y luego escribir en el cuadro de diálogo konsole, o xterm.


Saludos

---

### Post by tio lucas on 2011-03-10
no chiquillos, me refiero a la consola virtual

---

### Post by betitux on 2011-03-17
Yo también tuve ese problema y por más que modificaba el Grub, no podía setear el tamaño de las consolas virtuales (o sea Ctrl-AltF1, Alt-F2...Alt-F6). Finalmente mi solución fue con el comando setfont, de las cuales a las librerías de fuentes están en /usr/share/consolefonts/
Para modificar el tamaño de la letra usé el comando de la siguiente forma:

setfont /usr/share/consolefonts/Lat15-Terminus24x12.psf.gz

Dentro del directorio /usr/share/consolefonts podrás encontrar diversos tamaños y tipos de tipografías. Deberías probar el tamaño hasta que tu pantalla alcance el tamaño adecuado. Puedes incluir el comando "setfont" como primera línea del .profile del usuario para reconfigurar el tamaño de la consola virtual.
Espero haberte sido útil y saber si te ha servido mi solución.

Saludos

---

