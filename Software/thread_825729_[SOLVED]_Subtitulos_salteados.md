---
title: "[SOLVED] Subtitulos salteados"
date: 2008-06-11
forum: Software
---

### Post by Tosh78 on 2008-06-11
Hola gente! Les cuento que estoy con un problema con los subtitulos. Resulta que tanto el Totem como el VLC me saltean lineas (esto antes con el VLC no me pasaba). Ejemplo:
Si el archivo dice 
"hola, como estas?"
"Bien y vos?"
"Todo tranquilo"
Me aparece solo
"hola, como estas?"
Estuve leyendo y en un post encontre que USER21 comenta lo siguiente: 

Aquellos reproductores que "saltean" subtítulos, lo hacen por que el archivo no está en la codificación apropiada. Simplemente cambien las opciones de CODIFICACIÓN (de acuerdo a cada PLAYER) en Centroeuropeo o uno similar ( fijense de acuerdo al modo ISO que usa cada uno)... Ahora estoy en el trabajo, pero creo que, por ejemplo, el LATIN 1 es el ISO 8859-1/2 , los cuales muestran los ACENTOS y DIERESIS apropiadamente! De esta forma, NO TE SALTEARA MÁS los subs.

Otra solución? Editar el sub y convertirlo a esas mismas codificaciones.

MAS INFO EN [http://es.wikipedia.org/wiki/Codific..._de_caracteres](http://es.wikipedia.org/wiki/Codific..._de_caracteres)

El tema es que no se como convertir los subs editandolos, ni con que programa hacerlo, y tampoco se como cambiar las opciones de Codificacion del Totem ni del VLC. Alguien me puede dar una mano?

---

### Post by SLA_leandrin on 2008-06-11
Podés instalar gnome-subtitles;

```
 sudo apt-get install gnome-subtitles 

```

De todos modos, te comento que para que se vea bien el VLC, es suficiente con cambiarle la codificación de los subtítulos a CP1252 (que es la codifiación de WinChot), al menos en mi experiencia...

Espero te sirva, saludos.

EDIT: no había leido que no sabes como cambiar.

En VLC:

Opciones --> Preferencias --> Entrada/Codecs --> Otros codecs --> Subtítulos 

En Tótem:

Editar --> Preferencias --> En la pestaña general, abajo, está para elegir la codificación.

---

### Post by Tosh78 on 2008-06-11
Mil gracias, voy a probar!!

---

### Post by atatiducken on 2008-06-11
yo con **smplayer** nunca tuve problemas, si te interesa probalo es muy bueno

---

### Post by Mister X on 2008-06-11
Hay que pasarle esta solucion a los de Warner Channel

---

### Post by Thalskarth on 2008-06-11
> **SLA_leandrin said:**
> Podés instalar gnome-subtitles;

```
 sudo apt-get install gnome-subtitles 

```

De todos modos, te comento que para que se vea bien el VLC, es suficiente con cambiarle la codificación de los subtítulos a CP1252 (que es la codifiación de WinChot), al menos en mi experiencia...

Espero te sirva, saludos.

EDIT: no había leido que no sabes como cambiar.

En VLC:

Opciones --> Preferencias --> Entrada/Codecs --> Otros codecs --> Subtítulos 

En Tótem:

Editar --> Preferencias --> En la pestaña general, abajo, está para elegir la codificación.

Yo uso el VLC. Y existe aún una forma más sencilla.

Abri los subtitulos con el gedit (editor de textos)
pones guardar como y sobreescribi el arhico de subtitulos, pero fijate en la ventana abajo de seleccionar UTF-8.
Pones guardar y listo...


entonces, el VLC te los toma bien y funcionan sin drama

te adjunto imagen para que sea mas 'grafico'. :)

---

### Post by Tosh78 on 2008-06-11
Millones de gracias a ambos!!! Las dos cosas funcionaron perfecto!

---

