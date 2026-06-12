---
title: "Problema en Amarok 2  (problema de etiquetas)"
date: 2009-07-05
forum: Software
---

### Post by xc36e on 2009-07-05
Buenas 

No es de vida o muerte. Pero en esta nueva version de **Amarok** (la 2.0.2) tras conseguirme Ubuntu 9.04. Tengo un par de problemas, nose si alguien ya lo ha solucionado por eso lo hago publico aca.

El tema es que Amarok 2 no me reconoce los "**tag**" o **etiquetas** de mis archivos mp3 (la gran mayoria). Con lo que hace dificil la obtencion de las letras de las canciones, y tambien otros plugins como "lo que estoy escuchando", entre otros. Ademas q es muy incomodo a la hora de buscar canciones en el mismo Amarok ya que no las encuentra y hay que buscarlas manualmente.

Si pongo editar los detalles del track ("edit track detail"), me abre la pantalla para editar los tag y estan:
1) o completamente vacios (en blanco) ó 
2) No pudo editarlos, en gris (nose porque).

Ya a estas alturas me sería practicamente imposible re-etiquetar toda la fonoteca. :|

**Importante**: **Si puedo** ver los tag de las canciones mediante, por ejemplo, **exfalso** o **easytag** los metadatos de los archivos estan en lo correcto, con su nombre de cancion, artsta y albun en lo correcto. Por eso el problema se encuentra en el Amarok.

[U]No me acuerdo como se llamaba pero puede ser algun tema de eso que existen 2 tipos de tag, uno simple y otro extendido con mas etiquetas. (algo de eso..)
[/U]

Gracias

---

### Post by Hei Ku on 2009-07-05
Probá que pasa instalando la ultima version. Las instrucciones estan aca: [http://www.kubuntu.org/news/amarok-2.1](http://www.kubuntu.org/news/amarok-2.1)

Por otro lado, en mi caso la edicion de los tags no me funciona en la lista de la coleccion, pero sí en la lista de playlist.
Y JuK es mucho mejor para editar tags que Amarok, las opciones son mucho mas potentes.

---

### Post by xc36e on 2009-07-09
Hola vuelvo para decir que encontre la solucion, por si a algun otro newie como yo le pasa.

Instale la nueva version de Amarok2 y nada cambió. Siguió con lo mismo.

Ahora, y por esas casualidades de la vida, encontre que algunas carpetas (y nose porque) de la música se encontraban con permisos de root.

Busque un poco sobre chmod,
le di permisos de 775 y salió andando.

Siempre se aprende algo nuevo...

Lo bueno es que salio andando y ya vuelvo a confiar en Amarok :)

Saludos y gracias

---

