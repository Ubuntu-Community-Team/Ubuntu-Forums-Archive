---
title: "Problemas con plasma"
date: 2009-10-26
forum: Software
---

### Post by oktubrer on 2009-10-26
Buenas, ¿a alguno de los usuarios de KDE4 les pasó algo similar a esto?
[https://bugs.kde.org/show_bug.cgi?id=193176]("https://bugs.kde.org/show_bug.cgi?id=193176")

Para el que no entienda inglés, cuando quiero por ejemplo cambiar el wallpaper, desde las propiedades del escritorio, y voy al botón "Navegar" para examinar el disco en busca de las imagenes, se congela plasma (la ventana de propiedades, widgets, el panel).  La ventana la puedo cerrar, pero plasma sigue congelado hasta que se lanza la aplicación de reporte de bugs de KDE y se reinicia (o la reinicio a mano antes de eso).
Si a nadie le pasó algo similar o si le pasó pero no lo resolvió, voy a tratar de reabrir el reporte del bug.

---

### Post by pol666 on 2009-10-26
Mira a mi me pasaron muchas cosas, y crashes de plasma miles de veces, seguro hasta alguna vez me paso eso.. pero  a vos te pasa siempre?

---

### Post by oktubrer on 2009-10-26
Si si, no estoy seguro a partir de que actualización, si era el beta o ya en el RC de Karmic, pero pasa todas y cada una de las veces.  A su vez el componente "Acceso Rapido" no muestra ninguna carpeta, indistintamente de cual le configure, por lo que asumo que es algún problema de plasma al intentar acceder al disco rígido.

---

### Post by pol666 on 2009-10-26
Raro, raro.. Proba borrando la carpeta .kde que esta en tu /home  Mirá que se borra la configuración del escritorio..

---

### Post by oktubrer on 2009-10-26
> **pol666 said:**
> Raro, raro.. Proba borrando la carpeta .kde que esta en tu /home  Mirá que se borra la configuración del escritorio..

Hace dos días hice algo similar, creé un usuario nuevo, y andaba ok.  Lo empecé a configurar a mi gusto, y lo único que copié del home viejo fue la carpeta .opera.  Cerré sesión, y cuando volví a abrir pasaba exactamente lo mismo.  Quizás es alguna combinación de configuraciones, voy a probar un poco más.  Después les cuento.

---

### Post by guillermolisi on 2009-10-26
Que version de KDE y de Qt estas usando ?

Edit: Igual vi que la resolucion tomada fue marcada como invalida, asi que a seguir remando :)

---

### Post by oktubrer on 2009-10-30
Perdón por no responder.  Al final no hice absolutamente nada, actualice los paquetes que iba siendo necesario actualizar, y hoy se me dió por probar y funciona todo bien.  Sería algún bug del RC después de todo.  Solved!

---

