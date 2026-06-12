---
title: "ayuda con video por internet"
date: 2010-03-31
forum: Software
---

### Post by joseluis on 2010-03-31
No se que puede estar pasando. No puedo abrir ningún video que se transmita por internet, por ejemplo de Youtube o páginas de noticieros, para que se den una idea.
No es problema de conexión: en la maquina con windows funciona perfectamente y la velocidad está buena.
Las pantallas de los videos no muestran los controles, por ejemplo de avance o pausa. Y si se llega a ver algo...es muuuuuuuuuy trabado y lento, cortado.
Uso FF y Chrome, y pasa lo mismo en ambos, por lo que el tema es algo de conexión imagino.
Gracias a quienes puedan orientarme.

---

### Post by Applelnx on 2010-03-31
> **joseluis said:**
> No se que puede estar pasando. No puedo abrir ningún video que se transmita por internet, por ejemplo de Youtube o páginas de noticieros, para que se den una idea.
No es problema de conexión: en la maquina con windows funciona perfectamente y la velocidad está buena.
Las pantallas de los videos no muestran los controles, por ejemplo de avance o pausa. Y si se llega a ver algo...es muuuuuuuuuy trabado y lento, cortado.
Uso FF y Chrome, y pasa lo mismo en ambos, por lo que el tema es algo de conexión imagino.
Gracias a quienes puedan orientarme.

Tenes Flash instalado?
El resto de las paginas se cargan normalmente?

---

### Post by joseluis on 2010-04-01
tengo flash instalado. De hecho veo páginas con flash sin problemas. Las otras paginas de internet también se ven.

---

### Post by EnriqueK on 2010-04-01
¿Que estás usando, 32 bits o 64 bits?, si fuera el caso de que tienes 64 bits, lo mejor es descargar un flashplayerplugin experimental para 64 bits, pero funciona mejor que el que se instala normalmente que es de 32 bits, pero so lo fuerza a usarse en 64 bits, si este es tu caso, te puedo dar mas detalles para su descarga e instalación.

---

### Post by joseluis on 2010-04-01
tengo el ubuntu 9.10 de 64 bit

EDITO: Me diste la pista y busqué busqué busqué y encontré esta pagina 
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

que me ayudó. 
La recomiendo
Ahora veo bien los videos, pero en Chromme. FF sigue resistiéndose...no importa. Ya viene la 10.04!

gracias

---

### Post by EnriqueK on 2010-04-01
Para FF te lo explico rápido, entrá a la carpeta oculta _.mozilla _, te fijás si tenés una carpeta llamada **plugins**, si no es así, la creas y pones allí el archivo **libflashplayer.so**. que ya habrás descargado desde el sitio experimental de Adobe.
Es bueno hacer notar que solo para Linux Adobe tiene una versión para 64 bits, aunque sea experimental, funciona muy bien, para las otras plataformas , sigue la versión para 32 bits 
.

---

### Post by z37a on 2010-04-01
> **EnriqueK said:**
> Para FF te lo explico rápido, entrá a la carpeta oculta _.mozilla _, te fijás si tenés una carpeta llamada **plugins**, si no es así, la creas y pones allí el archivo **libflashplayer.so**. que ya habrás descargado desde el sitio experimental de Adobe.
Es bueno hacer notar que solo para Linux Adobe tiene una versión para 64 bits, aunque sea experimental, funciona muy bien, para las otras plataformas , sigue la versión para 32 bits 
.

Guarda que del 10.1 no tiene nada para 64 bits!!!!

Baja de aca el plugin:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Descargalo, descomprimilo y con permisos de admin lo copias en /usr/lib64/mozilla/plugins

Para hacer eso lo podes hacer mediante terminal haciando un "sudo cp libflashplayer.so /usr/lib64/mozilla/plugins/" sin las comillas, o haciendo Alt+F2 y luego "gksudo nautilus /usr/lib64/mozilla/plugins", luego arrastras y pegas el archivo alli dentro!

Esto te va a pasar en TODAS las versiones y distribuciones Linux de 64 bits!!!!!

PD: Espero que Adobe haga de una vez por todas el plugin 10.1 en AMD64 para linux!!!!!!

---

### Post by joseluis on 2010-04-02
esto lo he hecho, y no me funcionó. Es una lástima. FF se quedará en la cola por esto. Chrome lo toma bien, Opera también. Pero FF a pesar de hacer todos estos pasos varias veces...nada de nada

---

### Post by EnriqueK on 2010-04-02
> **joseluis said:**
> esto lo he hecho, y no me funcionó. Es una lástima. FF se quedará en la cola por esto. Chrome lo toma bien, Opera también. Pero FF a pesar de hacer todos estos pasos varias veces...nada de nada
Obviamente antes de hacer tofo esto tenés que desinstalar todos los Flash que hayas instalado antes y que son todos para 32 bits , como ser "flashplayer-installer" , gnash y todo lo que "huela"·a flash.

---

### Post by joseluis on 2010-04-02
ahora si!!!!!
seguro que era eso, desinstalé todo lo que "huele" a flash y volví a pegar ese archivo de adobe flash 64 y todo de 10
GRACIASSSSSSSSSSSSSSSSS

---

### Post by z37a on 2010-04-02
Cualquier cosa es muy útil saber que al entrar a firefox y hacer en la barra de direcciones "about : plugins"(todo junto pero si lo dejo junto sale una carita molesta!!!) podes ver todo lo instalado, de esa manera vas a ver los detalles de los plugins y los archivos que corresponde a cada uno!!!!

---

### Post by joseluis on 2010-04-05
muchas gracias "Z"

---

