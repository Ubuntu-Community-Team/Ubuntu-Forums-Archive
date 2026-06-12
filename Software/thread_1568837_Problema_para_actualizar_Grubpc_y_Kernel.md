---
title: "Problema para actualizar Grubpc y Kernel"
date: 2010-09-05
forum: Software
---

### Post by aregnando on 2010-09-05
Hola a todos, desde hace un tiempo que cada vez que entran actualizaciones al terminar de instalarlas me sale el siguiente mensaje de error:
E: grub-pc: el subproceso script post-installation instalado devolvió el código de salida de error 127
E: grub2: problemas de dependencias - se deja sin configurar
Desde que apareció esto tampoco me permitió actualizar el kernel.
Ya intenté desde Synaptic reinstalar grub-pc y grub2 pero no me deja y la verdad es que no se como solucionarlo.

---

### Post by guillermolisi on 2010-09-05
Cuando usas Synaptic no te dice que tenes paquetes rotos en el panel superior a la izquierda de la ventana con la lista de paquetes ?

---

### Post by juancarlospaco on 2010-09-06
E: grub2: **problemas de dependencias** - se deja sin configurar


problemas de dependencias, habria que ver la salida de un apt-get que dice...

---

### Post by aregnando on 2010-09-10
Guillermo, me fije en synaptic y en pauqetes rotos no figura nada.
No se si el origen de esto está en un arreglo del plymouth que intenté hace un tiempo en base a este tutorial:

[http://lavidalinux.com.ar/2010/05/como-arreglar-plymouth-en-ubuntu-10-04.html](http://lavidalinux.com.ar/2010/05/como-arreglar-plymouth-en-ubuntu-10-04.html)

Como no me dio ningún resultado regresé todos los valores a los anteriores pero es posible que haya arruinado algo en el proceso.

---

### Post by guillermolisi on 2010-09-10
Podrias explicar con el mayor detalle posible como regresaste todo a los valores originales ?

Tambien seria un buen aporte lo que sugirio Juan Carlos.

---

### Post by aregnando on 2010-09-15
> **guillermolisi said:**
> Podrias explicar con el mayor detalle posible como regresaste todo a los valores originales ?

Tambien seria un buen aporte lo que sugirio Juan Carlos.

Guillermo, según este tutorial había que cambiar algunos valores:

"Reemplazamos la línea 9

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

Por esto

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap”

Eso fue lo que hice, pero al ver que no tuvo ningún efecto volví a la linea original.

Luego en esta linea hice lo mismo:

"Reemplazamos la línea 18

#GRUB_GFXMODE=640×480

Por esto

GRUB_GFXMODE=1280×1024"

También volví a los valores que figuraban por defecto.

Con respecto a lo que sugiere Juan Carlos no se como fijarme los valores que devuelve el apt-get, soy usuario común y con un conocimiento bastante relativo, lo que si estoy totalmente convencido es que no me voy más de linux y mucho menos retornar a lo que tenía antes, por eso quiero tener mi Ubuntu andando a pleno y les agradezco toda la ayuda.

---

### Post by guillermolisi on 2010-09-15
Gracias por la explicacion.

Lo que Juan Carlos sugiere es abrir una terminal/consola e ingresar ```
sudo apt-get update
```y mostrarnos la salida en pantalla para saber en que paquetes te da este mensaje de advertencia.

---

### Post by josecuervo86 on 2010-09-15
Sabes donde puede estar el error? en **las comillas!**. Vos lo tenes asi:
```
GRUB_CMDLINE_LINUX_DEFAULT=**&#8221;**quiet splash**&#8221;**
GRUB_CMDLINE_LINUX_DEFAULT=**&#8221;**quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap**&#8221;**
```

pero deberia estar asi:
```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash**"**
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap**"**
```

Mas info aca: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/569272](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/569272)

Fijate tambien en las comillas que aparecen en la resolución

Cambia las comillas y hace:
```
sudo update-grub
sudo update-grub2
```

Un consejo que a mi por lo menos me sirve bastante a la hora de resolver problemas, busca en google el error que te tira la terminal, en este caso el **error 127 de grub**.

Saludos!

---

### Post by aregnando on 2010-09-16
> **josecuervo86 said:**
> Sabes donde puede estar el error? en **las comillas!**. Vos lo tenes asi:
```
GRUB_CMDLINE_LINUX_DEFAULT=**”**quiet splash**”**
GRUB_CMDLINE_LINUX_DEFAULT=**”**quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap**”**
```

pero deberia estar asi:
```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash**"**
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap**"**
```

Mas info aca: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/569272](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/569272)

Fijate tambien en las comillas que aparecen en la resolución

Cambia las comillas y hace:
```
sudo update-grub
sudo update-grub2
```

Un consejo que a mi por lo menos me sirve bastante a la hora de resolver problemas, busca en google el error que te tira la terminal, en este caso el **error 127 de grub**.

Saludos!

 Muchísimas gracias josecuervo86, finalmente era esto que me comentaste de las comillas, lo cambié y me dejó actualizar sin problemas, igualmente gracias Guillermo y juan carlos, esto es lo que hace que ame Linux y el foro de Ubuntu.
Un abrazo.

---

### Post by josecuervo86 on 2010-09-16
Me alegro que se haya resuelto el problemita! 

Saludos!

---

