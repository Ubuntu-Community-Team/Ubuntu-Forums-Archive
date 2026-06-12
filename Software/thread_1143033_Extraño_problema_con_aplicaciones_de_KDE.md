---
title: "Extraño problema con aplicaciones de KDE"
date: 2009-04-29
forum: Software
---

### Post by nemodot on 2009-04-29
Buenas,

Tengo un problema con las aplicaciones de KDE, exclusivamente con sus fuentes, no lo puedo describir bien por eso adjunto un pantallazo para que vean lo que me pasa:

---

### Post by pablo.s on 2009-04-29
Fijate la configuración de antialiasing
de las fuentes. Probá con cada parámetro
hasta que no te dé el problema.

EDIT: La configuración la debés modificar
desde el panel de control de KDE4, si no
lo descargaste, fijate todos los paquetes
que digan KDE control panel en Synaptic.

---

### Post by nemodot on 2009-04-29
El problema es que el panel de control se ve igual de mal. :S

---

### Post by pablo.s on 2009-04-29
Tendrías que desactivar el
antialiasing a mano, el tema
es que la última vez que utilicé
KDE fué en 2001...

Posiblemente algún usuario
de KDE tenga la manera para
deshabilitarlo ¿Alguien por ahi?

---

### Post by nemodot on 2009-04-29
Silencio desértico y cardos rodando por el suelo.:???:

---

### Post by pablo.s on 2009-04-29
No te angusties, acá hay gente muy
conocedora de KDE, como mi GRAN
AMIGO Hei Ku. En cuanto lean tu
problema vas a ver que algo van a
resolver. Yo no te puedo ayudar mas
porque desconozco de la anatomia
interna de KDE como para darte una
solución, lamentablemente utilizo
GNOME.
Saludos.

---

### Post by guillermolisi on 2009-04-29
> **nemodot said:**
> Buenas,

Tengo un problema con las aplicaciones de KDE, exclusivamente con sus fuentes, no lo puedo describir bien por eso adjunto un pantallazo para que vean lo que me pasa:
Disculpa la pregunta pero viendo en detalle el screenshot que adjuntaste el escritorio que hay detras de Amarok pareceria ser mas Gnome que KDE.

Es asi o solo lo tenes tan personalizado que parece solamente pero es un KDE "genuino" ?
Luego, si es todo KDE, que version estas usando ?

Lo que mas me llama la atencion es que las letras de los iconos en el escritorio se ven perfectas.

---

### Post by josecuervo86 on 2009-04-29
Eso que esta atrás definitivamente es GNOME!!. Pero por lo que pude entender tiene problemas con las aplicaciones de **KDE**, cuando las corre en **Gnome**

---

### Post by nemodot on 2009-04-29
Si, exactamente lo que dice JoseCuervo, es Gnome. El problema es con las aplicaciones de KDE que tengo instaladas y que muestro en el screenshot: VLC media player, Amarok 2 y QT 4 Settings.

---

### Post by guillermolisi on 2009-04-29
> **josecuervo86 said:**
> Eso que esta atrás definitivamente es GNOME!!. Pero por lo que pude entender tiene problemas con las aplicaciones de **KDE**, cuando las corre en **Gnome**
Bueno, por lo menos no estaba tan errado o no estoy tan solo en mi apreciacion sobre que era Gnome :)

Luego, que version de KDE (bibliotecas/librerias Qt) tenes instalada, la 4, la 4.2, etc.

Y digo, no le estara faltando algun font que usa KDE y por eso las dibuja como puede, antialiasing inclusive ?

---

### Post by josecuervo86 on 2009-04-29
Por lo que pude ver tiene amarok 2 asique si se los bajo de los repos oficiales no deberia tener las librerias de 4.2? Porque hasta la actualizacion a Jaunty solo estaba disponible la 1.4 (creo que era esa)

---

### Post by pablo.s on 2009-04-29
> **guillermolisi said:**
> Y digo, no le estara faltando algun font que usa KDE y por eso las dibuja como puede, antialiasing inclusive ?

Me juego la cabeza entera que es
un problema de antialiasing con
un orden de filtrado incorrecto...

El tema es ver una orden de consola
para que desactive el antialiasing
y aunque sea se vea algo.

---

### Post by pablo.s on 2009-04-29
Hete aqui que para desactivar antialiasing
"global" , mejor dicho para GNOME y KDE
hay que hacer esto:

Pasito a pasito:

1) Abrir una terminal

2)cd /etc/fonts/conf.d

3) sudo nano 10-antialias.conf

4)La linea que dice:
<edit name= "antialias" papapapapa sigue mas...
hay que cambiarle el parámetro que
dice "true" por "false"

5) Reiniciar las x

Ya está, va a quedar como un viejito...

---

### Post by nemodot on 2009-04-30
> **pablo.s said:**
> Hete aqui que para desactivar antialiasing
"global" , mejor dicho para GNOME y KDE
hay que hacer esto:

Pasito a pasito:

1) Abrir una terminal

2)cd /etc/fonts/conf.d

3) sudo nano 10-antialias.conf

4)La linea que dice:
<edit name= "antialias" papapapapa sigue mas...
hay que cambiarle el parámetro que
dice "true" por "false"

5) Reiniciar las x

Ya está, va a quedar como un viejito...

Lo hice, pero el problema persiste.

---

### Post by staar on 2009-04-30
mmmm parece ser este bug [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657"), probá cambiando las settings de suavizado DE GNOME, ponele el común, no LCD, o cambiando a RGB o BGR...

según el reporte del bug, la solución ya está, y el update te estaría apareciendo en las próximas horas ;-)...

saludos

---

### Post by pablo.s on 2009-04-30
U P D A T E :
Parece que es un problema de la
tarjeta de video. Acabo de leer en
un par de blogs en los que mucha
gente se queja del problema y
algunos han sugerido que probar a
ejecutar la aplicación KDE en
cuestión (por ej: Amarok) con la
terminal añadiendole el parametro
-low y esto funciona hasta que
lancen el parche.

Saludos.

---

### Post by nemodot on 2009-04-30
Ah, bueno, entonces esperaré. Tuve que reemplazar el Ktorrent que me gustaba tanto :(

Cómo hago para agregarle el parametro -low?

Probe de este modo pero da error:

```
esteban@esteban-desktop:~$ amarok -low
amarok: Unknown option 'low'.
amarok: Use --help to get a list of available command line options.
```

---

### Post by nemodot on 2009-04-30
Ciertamente la opcion "Subpixel (LCD)" es la que provoca esto.

La desactive y los apps de KDE van bien. Pero me gustan mucho las fuentes con esa opción asi que voy a esperar al fix.

Saludos, gracias a todos.

---

