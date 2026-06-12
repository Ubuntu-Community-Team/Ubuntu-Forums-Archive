---
title: "¿Cómo modifico el loader?"
date: 2009-09-04
forum: Software
---

### Post by GerryEastwood on 2009-09-04
Hola. Tengo un problema y espero que nadie se enoje por lo que pregunto, pero necesito cambiar el loader para que la PC me arranque por defecto en Windows y no en Ubuntu.

La cosa es que estoy haciendo un trabajo cotrarreloj y no tengo tiempo de buscar un programa en Ubuntu que reemplace a Adobe Premiere o Sony Vegas y encima aprenderlo.

Ocurre que enciendo las PC y si me distraigo un momento me inician en Ubuntu y tengo que salir y volver a entrar en Windows.

Gracias, espero que sepan comprender.

---

### Post by guillermolisi on 2009-09-04
Podrias mostrarnos como es el contenido de tu /boot/grub/menu.lst, asi podremos asesorarte mejor ?

---

### Post by anarko on 2009-09-04
En el archivo menu.lst ubicado en /boot/grub/
Tenes que modificar la linea que dice "Default    0" y poner el numero de orden donde esta ubicada la linea de inicio del windows. Las lineas son las que tiene la siguente forma : "title		Ubuntu 9.04, kernel 2.6.28-15-generic" esa es mi default 0 despues de eso tenes otras lineas asociadas al booteo de ese kernel, la default 1 seria la siguiente que comienza con "title"

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		cdfe24ac-04b2-4d29-9fca-880ae5498c95
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=cdfe24ac-04b2-4d29-9fca-880ae5498c95 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		cdfe24ac-04b2-4d29-9fca-880ae5498c95
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=cdfe24ac-04b2-4d29-9fca-880ae5498c95 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		cdfe24ac-04b2-4d29-9fca-880ae5498c95
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=cdfe24ac-04b2-4d29-9fca-880ae5498c95 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		cdfe24ac-04b2-4d29-9fca-880ae5498c95
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=cdfe24ac-04b2-4d29-9fca-880ae5498c95 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

```

En esta seccion seria :
default 0 = Ubuntu 9.04, kernel 2.6.28-15-generic 
default 1 = Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
default 2 = Ubuntu 9.04, kernel 2.6.28-14-generic
default 3 = Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)

Espero no ser confuso.

PD: Todo estolo tenes que hacer con el editor en modo superusuario "gksudo gedit"

---

### Post by Cajuma on 2009-09-04
Lo mas sencillo es instalar startupmanager desde los repos y con el cambias
en modo gráfico el arranque por defecto y la cantidad de Kernels 
(si tenés mas de uno) que quieras que aparezcan en el Grub.
Saludos. :D

---

### Post by SLA_leandrin on 2009-09-04
+1 startupmanager

Por cierto, no creo que nadie se ofenda. 
Saludos.

---

### Post by SLA_leandrin on 2009-09-04
+1 startupmanager

Por cierto, no creo que nadie se ofenda. 
Saludos.

---

### Post by GerryEastwood on 2009-09-04
Muchas gracias. Es que antes de instalar Ubuntu hice unas preguntas y alguien me contestó con ligeramente agresivo "no te confundas"

Por cierto, me encanta Ubuntu, lástima que no le pueda dedicar el tiempo que merece (por ahora).

Gracias de nuevo, lo pruebo.

---

