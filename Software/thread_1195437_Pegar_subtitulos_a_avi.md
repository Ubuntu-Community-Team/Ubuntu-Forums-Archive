---
title: "Pegar subtitulos a avi"
date: 2009-06-23
forum: Software
---

### Post by ramiro_md on 2009-06-23
Bueno gente voy a ser claro en lo que pido :P. Se qué para realizar a cabo la acción del titulo del post existe avidemux, lo se usar pero tengo un pequeño problema, a pesar que pongo codificación UTF-8 me come algunos caracteres del subtitulo :s Hay alguna otra opción que no sea avidemux o comandos ?.
Gracias,

---

### Post by Mauro22 on 2009-06-23
Por lo que se la mayoria trabaja con mencoder, asi que uses la GUI que uses, en el fondo usan mencoder...


Si te omite caracteres como ¿ á ñ  etc, es porque estas usando un tipo de fuente que no los tiene (para reproducir o para pegarlo)


Yo tengo peliculas con los subititulos pegados que aca me faltan los acentos y el ¿ pero en el DVD se ven bien .... :S

---

### Post by ramiro_md on 2009-06-24
Si, cuando yo veo la película desde SMplayer y cargo los subtítulos desde el archivo se ve bárbaro. Cuando los quiero pegar con avidemux en la vista previa se ven medios truncados :S. Estoy usando la fuente DejaVuSans, creo que es la que usa la mayoría...voy a probar con otra font y posteo a ver que pasa.
Un saludo y gracias.

Nota.- probé con Arial y algunas otras más y sigue truncando :S

---

### Post by biale on 2009-06-24
Usando VLC y Gstreamer siempre tuve que especificar ISO-algo en lugar de UTF-8. Y si ponía UTF-8 se perdían las vocales acentuadas y las ñ.

No estarás especificando la codificación al revés?    Saludos.

---

### Post by Hei Ku on 2009-06-24
El UTF-8 no tiene los caracteres españoles. Deberia ser ISO8990-1 o algo asi.

---

### Post by rvm4000 on 2009-06-24
La mayoría de los subtítulos en español están en formato ISO-8859-1.

El UTF-8 tiene todos los carácteres del español (y de muchísimos otros idiomas) pero si el subtítulo usa otra codificación, evidentemente no funcionará.

---

### Post by ramiro_md on 2009-06-24
Gracias por la aclaración, pero no me aparece la opción ISO :S. Las opciones son:
Arabig
Baltic
Chinese Tradicional
Chinese Simplified
Cyrilic
Latin 1 - Western Europe
Latin 2 - Central Europe
Greek
Hebreu
Sloven
Turkish
UTF-8
UTF-16
:)

---

### Post by rvm4000 on 2009-06-24
Prueba con "Latin 1 - Western Europe".

---

### Post by biale on 2009-06-24
Iso 8859-1 También conocido como Alfabeto Latino n.º 1 o ISO Latín 1.
Saludos...

---

### Post by ramiro_md on 2009-06-25
Gracias gente, con el "Latin 1 - Western Europe" al parecer salió andando. Por otro lado me gustaría que me dijeran, si alguno sabe, cuál es el color de los subtítulos ?...osea, amarillos si, pero cual es el código de color exacto o cual es el que usan ustedes.
Desde ya muchas gracias :)

---

