---
title: "Grave problema con las fuentes en Karmic"
date: 2010-01-03
forum: Software
---

### Post by daggaz on 2010-01-03
Hola.
Acabo de instalar Ubuntu Karmic de manera "limpia" por que tenía un verdadero desorden de particiones y necesitaba instalar Win$... Y bien todo parecía ir en orden hasta que comencé con la mudanza de los archivos respaldados y copié mis fuentes antiguas a la carpeta de fuentes del sistema (Usando Sudo Nautilus y llendo a */usr/shared/.fonts* o algo similar). No borré nada, unicamnete mezclé las carpetas y agergué las fuentes faltantes. En eso algunos de los títulos de las ventanas desaparecieron, así como los textos de los botones y otros más; en su lugar por cada caracter aparecía un rectángulo, como cuando uno ve una página de caracteres chinos y no tiene el codec para intepretarlos, pues así pasó; pensé en reiniciar y que con eso sería sufienciente, lo hice desde la terminal, ya que esta no se vio afectada por el problema, pero al reiniciar nada había cambiado; abrí Synaptic guiandome por el ícono, por que también las tipografías de los menús se volvieron rectángulos.[IMG]http://img213.imageshack.us/img213/8718/pantallazouo.png[/IMG]
Una vez ahí busqué la palabra "font" reinstalé la mayoría de los paquetes que tenían que ver... Reinicie y nada...
Decidí inciar con mi LiveUSB y desde aquí busqué en Google pero no encontré a nadie con el mismo problema. Así que vengo aquí a pedir ayuda. Logré hacer una captura de pantalla que adjunto aquí:



Espero me puedan ayudar, gracias.

---

### Post by daggaz on 2010-01-03
Bueno, tenía un caos en mi carpeta *fonts*, mezcladas fuentes del sistema y las mías. Lo que hice primero fue iniciar en el *LiveUSB* y copiar las fuentes de este a otro *pendrive*, reiniciar, entrar a mi Ubuntu en Disco Duro, ingresar de nuevo a la carpeta de *fonts* desde la terminal y reemplazar todo, pero no funcionó.
Lo segundo fue desde el LiveUSB borrar todo el contenido de la carpeta Fonts (de mi PC) vía *Sudo Nautilus* y reponerla con la carpeta *fonts* de mi LiveUSB. reinicié, limpié el caché en terminal y listo, todo volvió a la normalidad. Pondré mis fuentes en una carpeta nueva que llamare «usuario», espero funcione...

---

