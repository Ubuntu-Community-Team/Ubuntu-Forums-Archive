---
title: "Cómo editar la lista de Radios de Rhythmbox"
date: 2010-11-19
forum: Software
---

### Post by Pan0ramix on 2010-11-19
Dispongo del complemento de radio que viene en el reproductor de sonido Rhythmbox de 10.10 Maverick Meerkat y hay una opción para agregar url's de nuevas estaciones de radio, pero lamentablemente es de a una por vez.

Tengo una lista bastante extensa de radios que me gustaría disponer en el reproductor y no encuentro la fuente para editarla.
Alguien sabe como hacerlo? Quiero editar la lista y agregarle las radios que tengo en un txt.

Gracias de antemano. Postearé la solución ya que no la encuentro en los foros.

---

### Post by Mario Altamirano on 2010-11-19
Deberías localizar este archivo y editarlo.
rhythmdb.xml.
Ahi tenes no solo las radios sino tambien el listado de musica de tu maquina.
Tenes que saber editar XML.
Exitos.
Mario

---

### Post by Mario Altamirano on 2010-11-19
> **Mario Altamirano said:**
> Deberías localizar este archivo y editarlo.
rhythmdb.xml.
Ahi tenes no solo las radios sino tambien el listado de musica de tu maquina.
Tenes que saber editar XML.
Exitos.
Mario
Podes buscar el archivo, escribiendo en el Terminal lo siguiente:
find ~ | fgrep rhythm | fgrep playlist
o
find ~ | fgrep rhythm | fgrep rhythmdb

y te va a aparecer la ruta, conviene anotarla yluego de habilitar los archivos ocultos podras editar el archivo en cuestion.
Perdón por el desorden al contestar. 
Exitos
Mario

---

### Post by Pan0ramix on 2010-11-20
Gracias Mario, ya localicé el archivo que buscaba. ¿Cuál editor de XML utilizás o recomendás usar?

---

### Post by myqp on 2010-11-21
Hola, perdon que me enrometa pero por casualidad tendran la url para escuchar pop radio 101.5 de argentina desde el Rhythmbox? gracias:p

---

### Post by Pan0ramix on 2010-11-26
> **myqp said:**
> Hola, perdon que me enrometa pero por casualidad tendran la url para escuchar pop radio 101.5 de argentina desde el Rhythmbox? gracias:p

Aqui adjunto una lista de radios, entre las primeras la que estás buscando de Radio Pop.

---

### Post by Pan0ramix on 2010-11-26
Bueno, probados todos los medios para editar el xml pero no consigo trabajarlo como una "tabla" donde pueda ir agregando las url de las radios, que son muchas por cierto. En mi anterior post dejé un archivo de gedit para compartir direcciones.
Seguiré probando ahora mediante el uso de excel para abrir archivos xml; el problema es compilarlo después...

---

