---
title: "Howto: Integrar dialogo abrir archivo de KDE en firefox"
date: 2009-11-24
forum: Software
---

### Post by AlexDDR on 2009-11-24
Cuando salio opensuse 11.2 me di cuenta de inmediato que firefox usaba los dialogos de KDE para abrir los archivos, lo que es super cómodo, ya que se puede ver miniaturas de las imágenes en grande, lo que es especialmente útil cuando subes fotos a internet desde tu camara web cuando sus nombre solo números similares o son demasiadas, aparte de mejorar la integración del cada vez mejor kde4.

  Después de sumergirme en los ppa de Ubuntu encontré uno que soluciona esto muy bien.


Así que si usas KDE, para lograrlo en Ubuntu 9.10 hay que seguir los siguientes pasos:

- Abrir una consola (en este caso en kde  Konsole)

> 

sudo add-apt-repository ppa:debfx/firefox-kde

sudo apt-get update

 ##por seguridad desinstalar el firefox anterior###

sudo apt-get remove xulrunner-1.9.1 firefox-3.5 firefox-3.5-branding


 ## ahora  instalar la versión parcheada de opensuse-KDE ##

sudo apt-get install firefox-3.5-kde xulrunner-1.9.1-kde




Espero les resulte porque yo estoy de lo mas contento con los resultados, lo único que me pregunto es si en el repositorio ppa se seguirá actualizando a las versiones de firefox, pero que en todo caso los parches  son del fantástico equipo de kde de opensuse

adjunto una imagen de muestra de mi escritorio


Para desinstalar osea volver a la otra versión de firefox, solo hay que quitar el repositorio desinstalar los paquetes instalados y volver a instalar el firefox normal.


saludos y espero sus comentarios

---

