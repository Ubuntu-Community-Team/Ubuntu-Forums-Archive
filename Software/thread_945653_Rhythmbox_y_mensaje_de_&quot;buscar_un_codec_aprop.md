---
title: "Rhythmbox y mensaje de &quot;buscar un codec apropiado&quot;"
date: 2008-10-12
forum: Software
---

### Post by valucha on 2008-10-12
[COLOR="DarkOrchid"]Holaaa...

Ando ahora con una cosa rarisima.

Hace unos días agregué un cd que me prestaron a la librería del Rhythmbox e inicialmente no podía reproducirlos. Supuse que no tenía los codecs instalados así que fui al SYnaptic e instalé todo lo que dijera gstreamer :p. Acto seguido, pude escuchar las canciones.

Pero ahora resulta que cada vez que abro el Rhythmbox me aparece el mensaje de que si quiero buscar un codec, si le doy que sí, busca un rato y no encuentra nada, y si le doy que no aparece constantemente. Sé que no me falta nada porque no solo que tengo todos los codecs del mundo instalados, sino que adema&#347; puedo escuchar y ver todo sin problemas.

Por otro lado en Windows cuando abrí el otro día esa carpeta con las canciones me saltó un mensajito del antivirus diciendo que había un virus que encima se llamaba algo como "codec...", lo eliminé y el antivirus dejó de molestar. Supuse que con eso en Ubuntu se iba a solucionar el problema, pero no!... sigue ahi...

¿Qué puede ser? ¿Un virus que ataca Ubuntu o qué?-
Gracias por sus respuestas desde ya.
Saludossss

Vale[/COLOR]

---

### Post by majatu on 2008-10-13
Valucha puede ser que de verdad no tengas los codecs para abrirlo, a mi me ha pasado. Podes instalarte los paquetes de codecs de audio y video "gstreamer" que podes encontrar dentro de los repos de Ubuntu, una vez instalados te aseguro que te reproduce casi casi todos los formatos (aclaro que algunos de los paquetes gstreamer a pesar de ser gratuitos no son licencia libre, por lo que vas a tener que habilitar los paquetes no libres para encontrarlos).
Buscalos en el gestor para agregar/quitar programas antes que en synaptic, mas rapido de instalar jeje.

Un saludo y espero te sirva!

---

### Post by valucha on 2008-10-14
> **majatu said:**
> Valucha puede ser que de verdad no tengas los codecs para abrirlo, a mi me ha pasado. Podes instalarte los paquetes de codecs de audio y video "gstreamer" que podes encontrar dentro de los repos de Ubuntu, una vez instalados te aseguro que te reproduce casi casi todos los formatos (aclaro que algunos de los paquetes gstreamer a pesar de ser gratuitos no son licencia libre, por lo que vas a tener que habilitar los paquetes no libres para encontrarlos).
Buscalos en el gestor para agregar/quitar programas antes que en synaptic, mas rapido de instalar jeje.

Un saludo y espero te sirva!

[COLOR="DarkOrchid"]Tengo todo todo todo loque dice gstreamer instalado. :S[/COLOR]

---

### Post by Air23 on 2008-10-14
Me parece que tu problema es este bug:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566)

Por lo que vi, no hay una solucion muy buena. Entre ellas figura mover la carpeta con los archivos que originaron todo fuera de la libreria del Rhythmbox. Otra opcion seria desmarcar "vigilar mi fonoteca en busca de archivos nuevos" en editar>preferencias>musica. Segun lei, si haces esto dejaria de buscar los codecs cada vez que abrir el programa.

Mientras tanto podes probar otro reproductor, yo uso exaile que anda barbaro

---

### Post by valucha on 2008-10-14
[Color="DarkOrchid"]Bueno, gracias a ese bug que me dio Air, descubrí que tenía que mirar que onda los "errores de importación", y resulta que ahi encontre que una cancion .mp3 no tenia el codec apropiado, raro porque las otras .mp3 si las escucho. Traté de reproducirlo con el totem y vaya sorpresa, no se reprodució apareció otro error diciendo que me faltaba el "Decodificador Windows Media Audio 9", como esa canción no me gusta mucho, decidi eliminarla y acabar con el problema. En resúmen, es un bug, que no lo es tanto porque el problema es de la cancion, no del rhythmbox, tal vez no se haya copiado entera del cd o algo raro.
Gracias por su ayudita, yo habia encontrado un bug parecido pero en castellano y no tenia mucho que ver con lo que a mi me pasaba. Pero este me hizo darme cuenta de como era la cosa.


Saludos y solved [/Color]

---

### Post by bumux on 2009-09-08
Buenas noches.

Si no me equivoco, en el panel izquierdo cuando se tiene activado el buscar cambios en la biblioteca si encuentra un archivo que no reconoce por códecs, entoces lo muestra como error.

Cuatro  opciones veo yo:

1. Desactivar buscar cambios en biblioteca. (No lo recomiendo).
2. Borrar los archivos que no reconoce, si no interesan.
3. Buscar los codecs adecuados.
4. Convertir el fichero a un formato libre. (Ogg, Flac).


Un saludo.

---

### Post by SLA_leandrin on 2009-09-08
Por un momento pensé que Valucha había vuelto al foro... alguien sabe que pasó con ella??

---

