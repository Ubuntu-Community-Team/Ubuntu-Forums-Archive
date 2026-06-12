---
title: "Kernel 2.6.25"
date: 2008-07-12
forum: Software
---

### Post by Apipote on 2008-07-12
Hola a todos

Es posible instalar HH (que lleva el kernel 2.6.24) y luego de alguna manera, hacer un update al kernel 2.6.25 ??

Digo esto, pues dicho kernel, tiene un soporte mucho mayor de wifi.

Gracias.

---

### Post by atari130xe on 2008-07-12
Me suena a compilación....

---

### Post by Apipote on 2008-07-12
> Me suena a compilación....

O sea...pesadilla. Mejor esperar a Intrepid.

Gracias !!!

---

### Post by Mauro22 on 2008-07-12
Aca esta la lista de los kernels


[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)


No se si lo queres bajar y despues actualizarlo a mano. No se si se puede ni como ejejejje

---

### Post by llove on 2008-07-13
checkeate este thread  [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) .saludos

---

### Post by [P]oli on 2008-07-13
No me fijo mucho, pero creo que las actualizaciones automáticas de Ubuntu actualizaron el kernel a esa versión, nose si me equivoco :P

---

### Post by sergiom99 on 2008-07-13
yo lo tengo al dia con Adept y esta así:
```
 sergio@kubuntu:~$ uname -r
2.6.24-19-generic 
```

---

### Post by Apipote on 2008-07-13
Gracias !!

---

### Post by sdm_cacto on 2008-07-14
Si queres isntalar el Kernel 2.6.26 es facil:

sudo gedit /etc/apt.sources.list

Pones la opcion reemplazar q trae Gedit, para buscar todos los "hardy" y cambiarlos por "intrepid"

dsp recargas synaptic, buscas el kernel y lo actualizas.

Luego de esto revertis el proceso de cambiar los sources y listo.

---

### Post by Apipote on 2008-07-14
Ok. Veamos.
Gracias

---

