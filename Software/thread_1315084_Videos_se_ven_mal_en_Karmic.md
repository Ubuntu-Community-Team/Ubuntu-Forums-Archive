---
title: "Videos se ven mal en Karmic"
date: 2009-11-04
forum: Software
---

### Post by matias_tati on 2009-11-04
Hola me di cuenta que mis videos se ven espantosos desde que actualice y con los colores invertidos tipo azul.
Dejo una captura.

[[img]http://a.imagehost.org/t/0732/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0732/Pantallazo)

---

### Post by Mauro22 on 2009-11-05
Me acuerdo que eso ya esta posteado hace bocha... A ver si lo encuentro..


Era algo de la salida de video, proba con vlc e it cambiando la salida de video desde las preferencias.



Edit: aca esta [http://ubuntuforums.org/showthread.php?t=1120764&highlight=Videos+en+negativo](http://ubuntuforums.org/showthread.php?t=1120764&highlight=Videos+en+negativo)

---

### Post by matias_tati on 2009-11-05
En ese post se recomienda cambiar a la salida a xv y esa es la que estoy usando.

[[img]http://h.imagehost.org/t/0253/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0253/Pantallazo)

---

### Post by Mauro22 on 2009-11-05
Entonces ni idea. Probaste sin compiz??

---

### Post by matias_tati on 2009-11-05
Sin el efecto negativo si

---

### Post by luks911 on 2009-11-05
> **matias_tati said:**
> Sin el efecto negativo si

Si sin compiz anda bien, probá lo siguiente: en una terminal ejecutá
```
gstreamer-properties
```
Y en el cuadro de diálogo que te va a aparecer, en la parte de Salida de Video seleccioná la opción
```
X Windows System (no Xv) 
```o ```
X Windows System (sin Xv)
```
Ahora probá el video con compiz habilitado a ver si se ve bien.

---

### Post by matias_tati on 2009-11-05
No no. Me exprese mal. No es que anda bien sin Compiz. En realidad como lo desactivo? Todo compiz o solo el efecto negativo?

---

### Post by luks911 on 2009-11-05
> **matias_tati said:**
> No no. Me exprese mal. No es que anda bien sin Compiz. En realidad como lo desactivo? Todo compiz o solo el efecto negativo?

Ah, está bien.
El efecto negativo: vas a Sistema > Preferencias > Administrador de opciones de Compizconfig (si esto no está, instalá el paquete compizconfig-settings-manager para que aparezca) y en Accessibility tenés el efecto Negativo, lo desmarcás y listo. Si ya estaba desmarcado o aún sigue viéndose mal, desactivas todo compiz yendo a Sistema > Preferencias > Apariencia y en la pestaña Efectos visuales marcás ninguno.
Si algo de esto sirve, probá lo que te decía antes.

---

### Post by matias_tati on 2009-11-05
Solucionado abri el Totem y en las pre4ferencias puse restaurar valores por defecto o algo asi y en VLC hize lo mismo. Saludos!!!

---

