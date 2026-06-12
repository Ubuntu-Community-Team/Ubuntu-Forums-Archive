---
title: "restricted-extras, Medibuntu y sources.list"
date: 2009-10-30
forum: Software
---

### Post by aledruetta on 2009-10-30
Hola Comunidad!

Luego de realizar la instalación de KK, una de las primeras cosas que hice fue instalar los paquetes ubuntu-restricted-extras y w32codecs (previo agregado de repositorios Medibuntu)

Me surgieron dos dudas:

1.- Es necesario instalar los dos paquetes, o es suficiente con los restricted-extras? Depende la página que consultas, te recomiendan instalar uno, el otro o los dos, para poder reproducir todo tipo de contenido multimedia.

2.- Cuando instalé el repositorio Medibuntu, primero recurrí al que se supone es el nuevo método: en "Orígenes del Software, Otro software, Añadir --> ppa:medibuntu". Bueno, supuestamente lo agregó, pero después al hacer apt-get update daba error. Entonces seguí el antíguo método según la guía de dos blogs. El primero no funcionó y el segundo sí.
La cuestión es que me quedé pensando, después de tanto toqueteo, cómo habría quedado mi sources.list. Lo abrí con gedit y resulta que en ningún lugar aparece el repositorio de Medibuntu.

Dónde está, entonces?

Saludos.

---

### Post by Mauro22 on 2009-10-30
Desde la alpha 2, solo instalé el restricted... y hasta ahora pude reproducir todo lo que tengo, videos, musica, dvd, etc... el w32codecs... que trae?? (codecs de win32 :) ) pero... para que sirve? Que agrega que el restricted no?

---

### Post by EnriqueK on 2009-10-30
Antes creo que el metapaquete ubuntu-trstricted-extras  contenía todo, pero ahora no contiene los codecs prvativos, por eso se hace necesario recurrir a Medibuntu para descargarlos ya sea por w32codecs , w64codecs o mejor si empleas el metapaquete **non-free-codecs**
La tendencia actual es que las listas de fuentes de repositorios de terceros, como ser Medibuntu. se alojen en la carpeta **/etc/apt/sources.list.d** , de esta dorma se tiene mayor limpieza y mejor control de las fuentes de lostas de repositorios.

---

### Post by aledruetta on 2009-10-30
Gracias EnriqueK, los encontré.

---

### Post by staar on 2009-10-30
no se si funcionará medibuntu con el nuevo método para agregar ppas, porque no es un ppa, es un repo que no se aloja en launchpad...

el método oficial de medibuntu (está en su página), como ya te dijeron, es agregando un archivo en la carpeta /etc/sources.list.d/

saludos

---

### Post by guisheca on 2009-10-30
El w32codec (o w64codec) o vas a necesitar para reproducir, por ejemplo, archivos .rmvb, entre otros.

---

### Post by aledruetta on 2009-10-30
Gracias a Staar y Guisheca, también, por la info.  :popcorn:

---

