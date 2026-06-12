---
title: "Cambiar permisos ficheros de un directorio"
date: 2010-05-11
forum: Software
---

### Post by JoniJnm on 2010-05-11
Hola,

Pueden decirme qué comando usar para desactivar, de todos los archivos de un directorio, la opción "permitir ejecutar el archivo como un programa"?

---

### Post by guillermolisi on 2010-05-11
Y por que querrias hacer tal cosa ?

Ojo con manipular los permisos en forma masiva que despues las cosas comienzan a funcionar mal y nadie sabra por que. Personalmente y salvo poquisimas y especiales excepciones, nunca tuve que modificar permisos.

---

### Post by JoniJnm on 2010-05-11
Porque tenía un proyecto php en windows y al pasarlo a linux todos los archivos tienen esa opción marcada y quería quitarla (así, al dar doble click se abre el archivo, no pregunta si quiero ejecutarlo o no).

Sólo quiero cambiarlos para esa carpeta :-)

---

### Post by Mister X on 2010-05-11
hola desde la consola, situate dentro de la carpeta donde estan los archivos y hacé:

```
chmod a-x *

```

---

### Post by anarko on 2010-05-11
Y por las dudas, leete esto : [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by euzkoarima on 2010-05-12
También podes hacerlo desde la GUI. Al menos en gnome sería así.
Abrís la ventana con los archivos a cambiar. Seleccionás los archivos a los que querés cambiarle el permiso (si son todos con <ctrl>-A seleccionas "all" todos). Botón derecho en cualquiera de todos los archivos y elegís del menú que despliega "propiedades".
Solapa permisos y más bien por abajo aparece un checkbox que dice "permitir ejecutar el archivo como programa". Lo deschequeas y listo.

Edit: agrego, una vez seleccionados los archivos, en lugar de botón derecho también podés hacer <alt>-<ret> para que aparezcan la ventana de propiedades. Por <ret> me refiero a la tecla de nueva línea que está "junto con las letras" (no el enter del teclado numérico")

Saludos,
Eduardo

---

### Post by JoniJnm on 2010-05-12
Hola, gracias por las respuesta

No sé por qué, pero cuando uso
chmod a-x *
Desaparecen todos los archivos y carpetas del directorio (menos las carpetas root de ese directorio)

euzkoarima, el problema era que hay archivos e subcarpetas, he usado:[FONT=monospace]
[/FONT]find . -type f -print0 | xargs -0 chmod -x

Y me ha funcionado.

Saludos y gracias!

---

### Post by guillermolisi on 2010-05-12
Entonces pudiste solucionar tu inquietud ?

---

