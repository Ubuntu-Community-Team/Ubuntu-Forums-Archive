---
title: "[Problema] Google Earth en Karmic Koala (drivers &quot;3D&quot; instalados)"
date: 2009-12-12
forum: Software
---

### Post by matiaz on 2009-12-12
¿Qué tal gente? Sí, es mi primer posteo y ya les estoy mangueando servicio técnico. Entiendan que soy nuevo y todavía no puedo cooperar demasiado :D Voy a ver si me empiezo a pasear por el foro más seguido..

Vamos a los bifes. Tengo una GF4 Ti4200 con los drivers "nvidia-glx-96" (los que soportan mi placa), el xorg.conf configurado con Compiz andando de 10 y "glxinfo | grep direct"/"glxgears" corriendo sin problemas.

La aceleración 3D anda joya, salvo por el programita este que no pude hacer andar. Probé desactivando Compiz y la capa "Atmósfera", con una versión anterior y nada.

Ahora estoy usando el Google Earth 5.1 de los repositorios de medibuntu (también probé instalar el .bin descargado de su página oficial con el mismo resultado). Miren qué bien que se ve:

[[IMG]http://img193.imageshack.us/img193/7620/pantallazoby.th.png[/IMG]]("http://img193.imageshack.us/img193/7620/pantallazoby.png")

¿Alguna idea?

---

### Post by guillermolisi on 2009-12-12
Cuanta memoria RAM poseen la placa y la PC ?

---

### Post by matiaz on 2009-12-12
512 la PC - 128 la placa de video.

---

### Post by kornykyano on 2009-12-12
Yo intentaría tocando la configuración de Nvidia (nvidia-settings).

---

### Post by matiaz on 2009-12-12
¿Tocando qué kornykyano? La aceleración 3D anda 10 puntos, el problema solo está en Google Earth =/

---

### Post by Mauro22 on 2009-12-12
[http://www.ubuntu-es.org/?q=node/122572](http://www.ubuntu-es.org/?q=node/122572)

[http://groups.google.com/group/earth-free/browse_thread/thread/d2780ea050be50bd/c63a773a97c36e27?pli=1](http://groups.google.com/group/earth-free/browse_thread/thread/d2780ea050be50bd/c63a773a97c36e27?pli=1)

[http://www.versiontracker.com/php/feedback/article.php?story=20090511042631770](http://www.versiontracker.com/php/feedback/article.php?story=20090511042631770)


:popcorn:

---

### Post by kornykyano on 2009-12-12
tenes instalado nvidia-settings? ... este tiene diferentes opciones para modificar, proba de a uno y ve que pasa....es prueba y error. (sudo apt-get install nvidia-settings)

Probaste instalar el .bin desde la pagina oficial de Google?

---

### Post by guillermolisi on 2009-12-12
> **kornykyano said:**
> tenes instalado nvidia-settings? ... este tiene diferentes opciones para modificar, proba de a uno y ve que pasa....es prueba y error. (sudo apt-get install nvidia-settings)

Probaste instalar el .bin desde la pagina oficial de Google?
Previa copia bien resguardada el /etc/X11/xorg.conf original antes de probar :) cosa de poder hacer un rollback cuando la cosa se ponga mas complicada.

---

### Post by kornykyano on 2009-12-12
Para usar nvidia-settings no es necesario ser administrador, también es posible modificando el archivo .nvidia-settings-rc oculto en tu /home/USUARIO/.

---

### Post by matiaz on 2009-12-13
> **Mauro22 said:**
> [http://www.ubuntu-es.org/?q=node/122572](http://www.ubuntu-es.org/?q=node/122572)

[http://groups.google.com/group/earth-free/browse_thread/thread/d2780ea050be50bd/c63a773a97c36e27?pli=1](http://groups.google.com/group/earth-free/browse_thread/thread/d2780ea050be50bd/c63a773a97c36e27?pli=1)

[http://www.versiontracker.com/php/feedback/article.php?story=20090511042631770](http://www.versiontracker.com/php/feedback/article.php?story=20090511042631770)


:popcorn:
Gracias por los links, activar el modo seguro de gráficos desde las opciones del programa solucionó el problema ;)

Obviamente, gracias también al resto por responder. Ya había probado toquetear el "nvidia-settings" e instalar el Google Earth desde el archivo .bin. El error estaba en el programa.

---

