---
title: "¿cómo respaldo la biblioteca del rhythmbox?"
date: 2009-09-12
forum: Software
---

### Post by donmatas on 2009-09-12
Estimad@s ubunter@s trasandin@s:

me gustaría saber si es posible respaldar la biblioteca del rhythmbox. Me refiero a la información de cada pista (artista, álbum, género, etc) de manera que al reinstalar no tener que volver a ordenar todo.

muchas gracias 
DM

---

### Post by pablo.s on 2009-09-12
La información de cada pista
(supongo que hablamos de 
música en formato MP3, OGG
o similar) se guarda mediante
metadatos de formato ID3 dentro
de cada archivo. Quiere decir que
si guardas la información de cada
tema en cada archivo MP3, no hay
necesidad de backup.

---

### Post by donmatas on 2009-09-13
> **pablo.s said:**
> La información de cada pista
(supongo que hablamos de 
música en formato MP3, OGG
o similar) se guarda mediante
metadatos de formato ID3 dentro
de cada archivo. Quiere decir que
si guardas la información de cada
tema en cada archivo MP3, no hay
necesidad de backup.

gracias pablo, pero ¿cómo puedo hacer para guardar los cambios que hago en los archivos a través de rhthmbox en los metadatos ID3?

salud
DM

---

### Post by pablo.s on 2009-09-13
> **donmatas said:**
> gracias pablo, pero ¿cómo puedo hacer para guardar los cambios que hago en los archivos a través de rhthmbox en los metadatos ID3?


Si te refieres a la información de
nombre de tema, autor, etc., esa
información se guarda con el
programa con el que la ingreses,
(mientras no esté protegido para
escritura el archivo) ya sea el mismo
Rhythmbox o Exaile, Muine, sea
cual sea. La información queda
dentro del archivo, por lo general
en la cabecera, incrustada para
que la pueda leer tanto un programa
como un Ipod, un telefono celular,
un pasacassette, digamos todo tipo
de reproductores de audio.
No se si respondi bien la pregunta.

EDIT: Pongo ejemplos de pantallas
porque me hice adicto:

[IMG]http://h.imagehost.org/0206/Screenshot-Songbird.png[/IMG]

[IMG]http://h.imagehost.org/0855/Screenshot-Songbird-1.png[/IMG]

[IMG]http://h.imagehost.org/0757/Screenshot-Metadata_Editor.png[/IMG]

---

### Post by donmatas on 2009-09-13
compa.

se explica perfectamente. Es lo que he hecho con ryhtmbox (acompaño pantallazo). El problema es uqe ya me ha pasado anteriormente que si bien quedan grabados en alguna parte, cuando he tenido que reinstalar mi SO se pierden esos datos (tengo separado el /home del punto de montaje del SO)

saludos
M

---

### Post by Hei Ku on 2009-09-13
quedan en el archivo .mp3, no en el rythmbox. Salvo que te refieras a otra cosa, y no al tag ID3.

---

### Post by donmatas on 2009-09-13
> **Hei Ku said:**
> quedan en el archivo .mp3, no en el rythmbox. Salvo que te refieras a otra cosa, y no al tag ID3.

no quedan en el mp3, al menos editandolo desde el rythmbox, pues mis mp3 los tengo en el /home,que no lo toco al reinstalar el SO. Es por eso que necesito saber donde guarda rhytmbox esa info

saludos
DM

---

### Post by Hei Ku on 2009-09-13
pues quedan ahi, o en ~/.gnome2/rythmbox/, que tambien es tu home. Aunque por lo que leí, parece que ese programa tiene bastantes problemas con los tags. Verifica que uses el encoding correcto para grabarlos.

Por lo demas, tampoco tienes permisos para grabar en ningun otro lado salvo tu home, asi que tienen que estar ahi.

---

### Post by granjero on 2009-09-14
un buen programa para editar la metadata de los mp3 es el "easytag" a mi me dejo mi biblioteca hecha una pinturita.... lleva un poquito de trabajo pero vale la pena!

salud!

```
sudo aptitude install easytag
```

---

### Post by donmatas on 2009-09-14
> **granjero said:**
> un buen programa para editar la metadata de los mp3 es el "easytag" a mi me dejo mi biblioteca hecha una pinturita.... lleva un poquito de trabajo pero vale la pena!

salud!

```
sudo aptitude install easytag
```

buenísimo, claro qeu basatante pega... El fin de semana le daré una vuelta para ver si puedo trabajar por lotes

muchas gracias

DM

---

