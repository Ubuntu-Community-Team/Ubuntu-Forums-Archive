---
title: "Kdenlive-Problema al Renderizar."
date: 2009-09-13
forum: Software
---

### Post by daggaz on 2009-09-13
Hola.
Pues era muy feliz con Kdenlive hasta que surgió un horrible problema.
No puedo renderizar nada a ningún formato. Me sale el siguiente mensaje:
«Rendering of "video.avi" aborted, resulting video will probably be corrupted.»
Probé con muchos formatos y cosas por renderizar (incluso dejando solo una pantalla de color o texto) y nada. No encuentro la solución en internet, las páginas que he encontrado están en inglés y son poco claras : /
¿Alguien sabe sobre este problema? Ya he probado re-instalar pero aún no sé bien cómo hacerlo de manera definitiva por que no sirvió de nada. Según yo, tengo todas las dependencias instaladas.

---

### Post by guillermolisi on 2009-09-13
> **daggaz said:**
> Hola.
Pues era muy feliz con Kdenlive hasta que surgió un horrible problema.
No puedo renderizar nada a ningún formato. Me sale el siguiente mensaje:
«Rendering of "video.avi" aborted, resulting video will probably be corrupted.»
Probé con muchos formatos y cosas por renderizar (incluso dejando solo una pantalla de color o texto) y nada. No encuentro la solución en internet, las páginas que he encontrado están en inglés y son poco claras : /
¿Alguien sabe sobre este problema? Ya he probado re-instalar pero aún no sé bien cómo hacerlo de manera definitiva por que no sirvió de nada. Según yo, tengo todas las dependencias instaladas.
Recordas a partir de que circunstancia comenzo este problema ?
Tenes tooodos los codecs necesarios y suficientes instalados y actualizados ?

---

### Post by daggaz on 2009-09-21
Encontré esto y me funcionó (ahora no tengo tiempo pero si alguien lo traduce correctamente podría ser de utilidad):



> Hello, giraffe!
 This error depends on frei0r-plugins!, At first, uninstall frei0r-plugins, then you can launch kdenlive properly and you can run the config wizard.
Next, you should check the ffmpeg libraries such as libavformat, etc. with synaptic. ffmpeg libraries-"unstripped" version are required to render all formats such as HDV, mpeg, mp4, vidx, flush, h264. you can install these unstripped libraries using synaptic.
 After installing ffmpeg- unstripped libraries, you can render all formats properly. But, in this situation you can use limited transitions such as Composite, Wipe, Luma. You need frei0r-plugins to use all transition effect.
Next, you can install frei0r-plugins. kdenlive can be launched normally after installing fei0r-plugins, and you can edit everything normally. However, rendering will crash just after starting rendering in any format. Additionally, you can not run the config wizard due to the message of "MLT's SDL module not found". This error depends on the frei0r-plugins library,
/usr/lib/frei0r-1/facedetect.so
 So, rename the library as below,
sudo mv /usr/lib/frei0r-1/facedetect.so /usr/lib/frei0r-1/facedetect.so-bak
 After this, you can use all transitions and render all formats. Try it!


---

### Post by oromero on 2009-09-26
> **daggaz said:**
> Encontré esto y me funcionó (ahora no tengo tiempo pero si alguien lo traduce correctamente podría ser de utilidad):

Estaba en idéntica situación que vos, Kdenlive no renderizaba nada, desde hace algún tiempo. Afortunadamente tu hallazgo me condujo a la solución y puedo disfrutar nuevamente de esta utilidad.
Por otra parte, y aunque no soy experto traductor, voy a tratar de satisfacer tu solicitud. así que ahí va el intento.

"Este error proviene de frei0r-plugins. Primero desinstalar frei0r-plugins, luego lanzar Kdenlive y ejecutar el asistente de configuración.
Luego chequear las librerias ffmpeg como ser libavformat, y demás con synaptic.
Las librerias ffmpeg version "unstripped" son requeridas para renderizar formatos como HDV, mpeg, mp4, vidx, flush, h264. estas librerías pueden ser instaladas con synaptic.
Después de instaladas las librerías ffmpeg unstripped se podrá renderizar todos los formatos normalmente. Pero en esta situación solo pueden usarse limitadas transiciones como ser Composite, Wipe, Luma, se necesita frei0r-plugins para usar todos los efectos de transiciones.
A continuación debe instalarse frei0r-plugins. Kdenlive podra ejecutar y editar todo normalmente. Sin embargo, al renderizar se producirá un crash después de que haya iniciado esta en cualquier formato. Adicionalmente, se puede ejecutar el asistente de configuración el cual dará el mensaje "Módulo MLT's SDL no encontrado".
Este error depende de la libreria frei0r-plugins
/usr/lib/frei0r-1/facedetect.so
 Se debe renombrar la librería como sigue
sudo mv /usr/lib/frei0r-1/facedetect.so /usr/lib/frei0r-1/facedetect.so-bak
Después de esto, podrá usar todas las transiciones y renderizar todos los formatos. Intentalo."

Bién esta es mi traducción, espero sea de utilidad, ya que en mi caso hacía más de dos meses que no podía renderizar nada con kdenlive y ahora lo tengo como de estreno otra vez.
Muchas gracias!!!

---

