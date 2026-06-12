---
title: "[SOLVED] Problemas con VirtualBox"
date: 2008-05-20
forum: Software
---

### Post by vk-cdg on 2008-05-20
Buenas, tengo un problema con VirtualBox, pero no estoy del todo seguro de donde proviene, si del SO Host (Ubuntu), si del SO Guest (XP) o si del propio VirtualBox. Paso a contar:

Ubuntu 8.04 actualizado al día!
VirtualBoc PUEL 1.6
Guest additions ultima versión

Problema 1: No puedo configurar en el SO invitado (XP) una resolución mayor a 1024x768. Tampoco "acomoda" la resolución de pantalla al tamaño y forma de la ventana de VirtualBox. Esto sucede desde que actualicé Guest additions a la última versión. Me faltó configurar algo?

Problema 2: No puedo compartir carpetas desde el SO Nativo (Ubuntu), me sale un error 225 algo. Cuando "sharié" la carpeta no me pidió instalar nada de Samba, por lo que asumo que estaba instalado. En el Synaptic lo veo instalado.

[IMG]http://tuxlink.files.wordpress.com/2008/05/compartir-3.png?w=392&h=642[/IMG]

Me queda como prueba desinstalar Samba y volver a instalarlo.

Haciendo un sudo nautilus puedo sharear las carpetas, pero desde el SO invitado no las veo.

Llevo mas de media mañana visitando blogs y foros por este tema pero para 8.04 no hay mucho de compartir carpetas con mi problema.

En este blog hay un procedimiento que no fue el que yo seguí, así que esta noche cuando llegue a casa probaré eso, previa desinstalación de Samba, a ver si con eso sale andando.

[http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/#comment-1943](http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/#comment-1943)

---

### Post by niko_3100 on 2008-05-20
sharear?? No querras decir compartir?? Si lo que queres es ver del xp al ubuntu en las opciones el virtual box te dice de instalar un programa para qeu el xp vea las carpetas y elegís las carpetas que querés compartir finalmente hacés: botón derecho sobre mi pc
 conectar a unidad de red, examinar, virtual box y la carpeta que quieras.

---

### Post by vk-cdg on 2008-05-20
Sharear o compartir los tomo como sinónimo, mas allá de que pueda estar mal escrito. 

Volviendo al punto, todo esto estaba funcionando  antes de instalar la versión 1.6 del VirtualBox y la ultima versión del Guest Additions. 
Antes de esta actualización, veía mis tres carpetas compartidas de mi ubuntu en el windows virtualizado.

El post lo armé ya que antes andaba y ahora no. Hice lo mismo que había hecho antes y nada. Mas aún, seguí varios tutos para hacer esto en Hardy sin resultados exitosos.

---

### Post by ariel on 2008-05-20
> **vk-cdg said:**
> Buenas, tengo un problema con VirtualBox, pero no estoy del todo seguro de donde proviene, si del SO Host (Ubuntu), si del SO Guest (XP) o si del propio VirtualBox. Paso a contar:

Ubuntu 8.04 actualizado al día!
VirtualBoc PUEL 1.6
Guest additions ultima versión

Problema 1: No puedo configurar en el SO invitado (XP) una resolución mayor a 1024x768. Tampoco "acomoda" la resolución de pantalla al tamaño y forma de la ventana de VirtualBox. Esto sucede desde que actualicé Guest additions a la última versión. Me faltó configurar algo?

Problema 2: No puedo compartir carpetas desde el SO Nativo (Ubuntu), me sale un error 225 algo. Cuando "sharié" la carpeta no me pidió instalar nada de Samba, por lo que asumo que estaba instalado. En el Synaptic lo veo instalado.

[IMG]http://tuxlink.files.wordpress.com/2008/05/compartir-3.png?w=392&h=642[/IMG]

Me queda como prueba desinstalar Samba y volver a instalarlo.

Haciendo un sudo nautilus puedo sharear las carpetas, pero desde el SO invitado no las veo.

Llevo mas de media mañana visitando blogs y foros por este tema pero para 8.04 no hay mucho de compartir carpetas con mi problema.

En este blog hay un procedimiento que no fue el que yo seguí, así que esta noche cuando llegue a casa probaré eso, previa desinstalación de Samba, a ver si con eso sale andando.

[http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/#comment-1943](http://tuxlink.wordpress.com/2008/05/09/compartir-carpetas-en-ubuntu-804/#comment-1943)



Sin problemas aca con 1.6 en ubuntu 8.04 / 64 bits. Hace tiempo ya que no hace falta samba para compartir carpetas en virtualbox. No hace falta usar "compartir carpetas" en nautilus ni nada de eso.

No se bien que es PUEL, yo uso la version binaria (no-open-source), en ingles. En esta version, cuando corre la VM, anda a "Devices", despues Shared Folders, es trivial. En el guest XP, abri un file explorer > Map Network Drive, asigna una letra, y escribi el nombre del folder: \\vboxsvr\nombre-que-eligiste

Con el tema de la resolucion, no tengo problemas tampoco. Siempre uso right-control-g, que cambia la resolucion del guest automáticamente.

---

### Post by vk-cdg on 2008-05-21
Bueno, finalmente encontré solución al problema.

Respecto de la resolución de pantalla, te juro que no puedo creer que sea tan salame de no ver la opción CTRL + G, pero bue.:(

Respecto de las carpetas compartidas, acá me llevó un poco mas de tienpo. La solución fue mas o menos así.

Luego de trarar de mapear unidades a mano y graficamente descubro que el equipo servidor no es vboxsrv sino Sion (el nombre de mi PC). Traté de conectar a mano y nada, finalmente probé hacer un \\Sion y me pide usuario y password, probé con el usuario y passowrd con los que accedo a Ubuntu y me mostró el contenido, conecté las unidades y listo. Todo funcionando.

Agrego un par de capturas para que lo vean.

---

### Post by Mauro22 on 2008-05-21
Que lindo que es ver a windows corriendo como si de un programa mas se tratase......


:lolflag:

Notaron que el virutalizado no se cuelga ni da pantallos azules...

---

