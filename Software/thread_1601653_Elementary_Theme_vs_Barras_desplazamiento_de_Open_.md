---
title: "Elementary Theme vs Barras desplazamiento de Open Office"
date: 2010-10-20
forum: Software
---

### Post by aledruetta on 2010-10-20
Hola Comunidad!

Problema: desaparecen las barras de desplazamiento en OpenOffice cuando está activado el tema Elementary.

Otros datos: Ubuntu Maverick - Elementary ppa.

¿Alguna sugerencia?
Gracias.

---

### Post by aledruetta on 2010-10-20
Dejo una captura del problema.

---

### Post by martin_legion on 2010-10-21
Tengo el mismo problema. Si encuentro la solución te la comento por aquí.

---

### Post by martin_legion on 2010-10-21
Por lo que veo de momento no hay solución. En los comentarios hay una respuesta de sólo 5 horas de antigüedad diciendo que se puede intentar modificar el tema (el elementary entiendo, no el openoffice) para incluír "steppers", pero no tengo ni idea de lo que es eso.

[http://danrabbit.deviantart.com/art/elementary-gtk-theme-83104033](http://danrabbit.deviantart.com/art/elementary-gtk-theme-83104033)

---

### Post by aledruetta on 2010-10-21
Bueno, habrá que esperar, entonces. Cualquier cosa, nos avisamos.

---

### Post by aledruetta on 2010-10-25
Agrego que el problema lo detecté con Elementary Theme, pero que ahora me doy cuenta que sucede lo mismo con otros temas, no con todos, pero con algunos sí. Es decir no es un problema particularmente de Elementary, tal vez sea de algún engine o del propio OpenOffice.

---

### Post by martin_legion on 2010-10-26
> **aledruetta said:**
> Agrego que el problema lo detecté con Elementary Theme, pero que ahora me doy cuenta que sucede lo mismo con otros temas, no con todos, pero con algunos sí. Es decir no es un problema particularmente de Elementary, tal vez sea de algún engine o del propio OpenOffice.

Sí, por lo que estuve leyendo yo llegué a la misma conclusión, parece que es algo del OpenOffice. 
Por cierto, OpenOffice es un proyecto en decadencia, y será de alguna  manera continuado en LibreOffice. Ya se puede descargar un Beta que he probado y me funcionó muy bien. Creía recordar que el LibreOffice no tenía el problema de las barras, pero tuve que instalar unos paquetes del openoffice y ahora veo que sí pasa lo mismo, pero no sé si es culpa de los paquetes o de mi mala memoria (siempre tuvo el problema)
Como sea, yo creo que va a haber más desarrollo en LibreOffice que en OpenOffice, así que no viene mal ir probándolo e involucrarse en ese proyecto.

Yo seguí los pasos de esta web sin problemas:
[http://gamblis.com/2010/10/11/how-to-install-libreoffice-on-ubuntu-maverick-meerkat-10-10/](http://gamblis.com/2010/10/11/how-to-install-libreoffice-on-ubuntu-maverick-meerkat-10-10/)

Saludos

---

### Post by martincasc on 2010-11-30
Bueno, espero no sea demasiado tarde para la respuesta/solución.

Leyendo por acá vi algo que decía *sttepers*. De forma tal que me puse a revisar el post en deviantART... Tras hacerlo bastó con mirar unos minutos el archivo de configuración del Theme, el archivo es el ***gtkrc*** (todos los themes son manejados por un archivo del mismo nombre). Aclaro, no tengo siquiera cero conocimiento en la creación de themes.

Bueno, la cosa es editar tal archivo, si lo tenes en tu *~/.themes/elementary/gtk-2.0/* no hay problema ya que no precisas de permisos root.

Para quienes como yo hayamos instalado el theme desde repositorios, el mismo se instalará en */usr/share/themes/* asique a editar el archivo.

Alt + F2 y tipeamos ```
gksu nautilus /usr/share/themes/elementary/gtk-2.0/
```

Otra forma de editar el archivo: ```
sudo gedit /usr/share/themes/elementary/gtk-2.0/gtkrc
```

... le damos Enter ... metemos nuestro pass ... y editamos el archivo gtkrc con Gedit o nuestro editor de preferencia. Buscamos por las siguientes lineas:

[HTML]GtkScrollbar		::has-backward-stepper 			= 0  
GtkScrollbar		::has-forward-stepper			= 0[/HTML]


Y **cambiamos el "0" por el "1"** y guardamos. Reiniciamos sesión, o recargamos el theme y problema resuelto. Al menos en ninguna otra aplicación he tenido problemas y ya está elementary funcionando. Siendo una solución tan simple, sabiendo los desarrolladores cuál es la solución y dada la excelencia de estos y el theme, no entiendo por qué no es incluida de serie. Por ello tomar la precaución de que el resto del theme funcine perfecto. Yo llevo unas horas y ningún problema, esperemos que siga así.

[IMG]http://img812.imageshack.us/img812/78/seleccin001.png[/IMG]

Saludos!

---

### Post by martin_legion on 2010-12-01
Muchas gracias por esta solución. Realmente es raro que siendo tan simple la solución no se haya sacado un parche un poco más automatizado para solucionarlo.

De nuevo, muchas gracias.

Un saludo

---

### Post by jacoborus on 2010-12-01
Gracias, no sabía que podía provocar el fallo.
No se ha resuelto en Elementary porque realmente es un fallo de OpenOffice, que no muestra la barra de scroll si esta no tiene las flechas (steppers) visibles (1=true=visible), estas se ocultaron en el theme porque casi nunca se usan, ya que todo el mundo arrastra la barra o hace un simple click para avanzar de página en página.

Otra solución sería poner las flechitas en la parte de abajo del scrollbar con:

```
GtkScrollbar ::has-forward-stepper = 1
GtkScrollbar ::has-backward-stepper = 0
GtkScrollbar ::has-secondary-forward-stepper = 0
GtkScrollbar ::has-secondary-backward-stepper = 1
```

---

### Post by martincasc on 2010-12-03
Así es, el fallo es de openoffice, si es que podríamos llamarlo fallo.

La solución que propone **jocoborus** es realmente muy buena, nos deja un estilo Mac OS con las flechitas *(steppers)* abajo.

Me he contactado con Daniel, el desarrollador de elementary Theme y me ha dicho que posiblemente se introduzcan variantes en el código del theme para trabajar directamente sobre OpenOffice. Esto es algo que vemos -por ejemplo- en Ambiance y/o Radiance.

Saludos!

---

### Post by adrian0301 on 2011-09-21
Muy útil y fácil :D

---

