---
title: "Problema de brillo al actualizar con MSI u100"
date: 2009-11-02
forum: Software
---

### Post by Kernel Loco on 2009-11-02
Hola,
Actualicé mi netbook MSI u100 a la nueva versión 9.10 y cada vez que se carga el sistema operativo, aparece el control de brillo y automáticamente se baja todo el nivel de brillo y después se vuelve a subir. Esto provoca un parpadeo en la pantalla durante unos 5-10 segundos. Después desaparece y todo queda normal (?). ¿A alguien le pasó? ¿Existe solución?
Gracias.

---

### Post by jemaydup on 2009-11-05
estimados cada vez que inicio mi pc la mantalla parpadea con el brillo osea sube y baja solo el brillo de mi netbook
esto me lo hace desde que instale 9.10 y sinceramente me preocupa porque obiamente es un problema de soft pero no quiero que me arruine el display cualquier consejo o configuracion posible se las agradesco.

mi netbook es una msi wind u100 :confused::?

---

### Post by josecuervo86 on 2009-11-05
Hola jemaydup, por lo que estuve viendo [0] y [1] parece ser un bug del gnome-power-manager y supuestamente pareciera que la bateria se conecta y desconecta causando que suba y baje el brillo de la pantalla. Fijate si estos reportes te sirven:

[0] [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131)

[1] [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/151675](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/151675)

---

### Post by pablitotm on 2009-11-05
> **Kernel Loco said:**
> Hola,
Actualicé mi netbook MSI u100 a la nueva versión 9.10 y cada vez que se carga el sistema operativo, aparece el control de brillo y automáticamente se baja todo el nivel de brillo y después se vuelve a subir. Esto provoca un parpadeo en la pantalla durante unos 5-10 segundos. Después desaparece y todo queda normal (?). ¿A alguien le pasó? ¿Existe solución?
Gracias.

Te cuento que yo tengo el mismo problema en la misma netbook... y no encuentro en ningun lado solucion alguna.. pues me sumo al pedido... otro problema es cuando se activa la camara web... cuando se hace lo dicho... no se pueden usar mas los puertos USB... alguien tiene una solucion a esto??

---

### Post by jeko37 on 2009-11-17
Este problema es ocacionado por un demonio llamado gnome-power-manager, lo que hay que hacer es deshabilitarlo al inicio del sistema, para ello van a SISTEMA -> PREFERENCIAS -> Aplicaciones al Inicio y buscan el item GESTOR DE ENERGIA, lo deshabilitan y listo, problema solucionado.

Suerte!

A mi me funciono con una MSI WIND U120.

---

### Post by guillermolisi on 2009-11-17
> **jeko37 said:**
> Este problema es ocacionado por un demonio llamado gnome-power-manager, lo que hay que hacer es deshabilitarlo al inicio del sistema, para ello van a SISTEMA -> PREFERENCIAS -> Aplicaciones al Inicio y buscan el item GESTOR DE ENERGIA, lo deshabilitan y listo, problema solucionado.

Suerte!

A mi me funciono con una MSI WIND U120.
Ese daemon no administra el consumo de bateria tambien ?

---

### Post by jeko37 on 2009-11-17
> **guillermolisi said:**
> Ese daemon no administra el consumo de bateria tambien ?

Seguramente, por eso dije "solucion parcial" hasta que venga alguna actualizacion que lo solucione, igual por mi parte estoy mirando a ver si lo puedo arreglar, en todo caso ya posteare.

---

### Post by pablitotm on 2009-12-15
En LPad un user ha creado una especie de parche ante este problema, si alguien es tan amable de explicar como se hace para corregir el problema estaría muy agradecido, ya que soy nuevo en Ubuntu, los links son los ya posteados...

---

### Post by guillermolisi on 2009-12-16
> **pablitotm said:**
> En LPad un user ha creado una especie de parche ante este problema, si alguien es tan amable de explicar como se hace para corregir el problema estaría muy agradecido, ya que soy nuevo en Ubuntu, los links son los ya posteados...
Estuve leyendo los dos links, el segundo esta considerado duplicado del primero, y esta bastante controvertida la cosa, ademas de antigua porque se inicio con Gutsy (2007).

Algunos dicen que el problema esta resuelto (fix released 2008-02-03), otros que no. Algunos tuvieron buenos resultados con ese "workaround" y otros no. Otros usaron acpi_fakekey en la linea de booting del Grub (los primeros casos, con Gutsy y las primeras versiones de Hardy).

En definitiva, las soluciones propuestas en LP me parecen demasiado antiguas y las entradas mas recientes (2009) aun no tienen comentarios concretos como para aplicar alguna solucion, ademas de que todas parecen estar relacionadas con una marca y modelo de maquina en particular. Todo esto fundamentado en que desde esa epoca a la fecha han cambiado las versiones del kernel, Gnome (g-p-m/gdm) y Xserver, lo cual no es poca cosa.

---

### Post by jeko37 on 2009-12-18
Un amigo encontro una solucion a esto, desinstalo el gnome-power-manager, el demonio que ocaciona ese problema, e instalo el power manager del Xfce y se le soluciono.

Doy fe que funciona porque lo vi, cuando lo haga en mi msi wind u120 les hago un step by step de como se hace.

Saludos

---

### Post by jeko37 on 2009-12-21
chicos encontre la solucion!

como comente arriba...

primwero desinstalan el gnome power manager, que es el proceso que ocaciona el bug

sudo apt-get remove gnome-power-manager

y luego reinician e instalan el administrador de energia del xfce

y sudo apt-get install xfce-power-manager

SALUD Y LIBERTAD!

---

### Post by jeko37 on 2009-12-23
no funciona con las u120... aunque si con las u123 :(

---

### Post by tidida on 2010-01-01
En [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/415023?comments=all](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/415023?comments=all) , ofrecen otra solucion es un parche para gnome-power-manager. A mi me funcionó (tengo el msi u100) os dejo el enlace al paquete debi [http://kamisama.free.fr/transfert/gnome-power-manager_2.28.1-0ubuntu1local1_i386.deb](http://kamisama.free.fr/transfert/gnome-power-manager_2.28.1-0ubuntu1local1_i386.deb)

---

### Post by jeko37 on 2010-01-07
confirmo que funcion para la u120 tambien! gracias loco!

---

### Post by jasmrael on 2010-07-28
> **jeko37 said:**
> Un amigo encontro una solucion a esto, desinstalo el gnome-power-manager, el demonio que ocaciona ese problema, e instalo el power manager del Xfce y se le soluciono.

Doy fe que funciona porque lo vi, cuando lo haga en mi msi wind u120 les hago un step by step de como se hace.

Saludos

Acabo de hacerlo y prendió perfectamente!!! Por fin !!
Estaba podrido con el blinking ese.
Gracias!!!

---

