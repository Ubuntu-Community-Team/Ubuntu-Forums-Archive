---
title: "Avidemux y MPEG4"
date: 2009-12-19
forum: Software
---

### Post by z37a on 2009-12-19
Hola gente, necesito hacerles una consulta. Ultimamente me estoy volviendo un poco loco para pasar mis videos a mi nuevo telefono. El telefono solo reproduce MPEG4, y siempre utilize MPEG4 ASP (lavc) en Avidemux. __Hace poco realize una prueba, en la cual ripie parte de un dvd utilizando K9copy y ffmpeg en mpeg4 y me funciono de 10 siempre y cuando respete la resolucion maxima del telefono. Ahora como puedo encodear con avidemux utilizando las misma caracteristicas que usa el K9Copy.

Segun lei en un thread de Debian deberia reemplazar lavc pro mpeg4 peor la verdad ni idea, no encuentro como.([http://www.debianhelp.org/node/4474](http://www.debianhelp.org/node/4474))

---

### Post by z37a on 2009-12-27
Bien logre poder pasar los vídeos a MPEG4, para ello utilice el codec xvid, hay una opcion dentro que es la de usar h263 y a la hora de grabar el archivo utilice mp4, de esta manera pude convertir mis vídeos al formato que utiliza el Nokia N97, así que si alguno pasa por lo mismo utilice el avidemux con esos codec que funciona, lo único no superar nunca la resolución máxima del teléfono 640x480(recomiendo aplicar un filtro para 640x360 para verlos en pantalla completa).

PD: No se como ponerle el SOLVED al titulo del tema!!!!!

---

### Post by giovannivl on 2009-12-29
> **z37a said:**
> Bien logre poder pasar los vídeos a MPEG4, para ello utilice el codec xvid, hay una opcion dentro que es la de usar h263 y a la hora de grabar el archivo utilice mp4, de esta manera pude convertir mis vídeos al formato que utiliza el Nokia N97, así que si alguno pasa por lo mismo utilice el avidemux con esos codec que funciona, lo único no superar nunca la resolución máxima del teléfono 640x480(recomiendo aplicar un filtro para 640x360 para verlos en pantalla completa).

PD: No se como ponerle el SOLVED al titulo del tema!!!!!

Hola, estoy intentando lo mismo, y me ha salido el asunto, me ayudarias con algunos print-screens de tu configuracion por favor, lo mejor que he logrado es que suene el video, pero no se ve nada en pantalla, gracias!

---

### Post by z37a on 2009-12-29
> **giovannivl said:**
> Hola, estoy intentando lo mismo, y me ha salido el asunto, me ayudarias con algunos print-screens de tu configuracion por favor, lo mejor que he logrado es que suene el video, pero no se ve nada en pantalla, gracias!

Acá te dejo el print del source, elegí un video en 720p así podes ver como redimencionarlo:

[IMG]http://img85.imageshack.us/img85/2384/pantallazo1xo.png[/IMG]

Luego abro el avidemux y abro dicho video, fijate en la izquierda las opciones que seleccione:

[[IMG]http://img85.imageshack.us/img85/8851/pantallazo2r.th.png[/IMG]](http://img85.imageshack.us/i/pantallazo2r.png/)

**Nota,** fijate que seleccione el codec **MPEG4-ASP (xvid)**, audio **AAC**, y formato **mp4**

Ahora configuro el codec de video de esta manera:

[IMG]http://img63.imageshack.us/img63/6358/pantallazo3b.png[/IMG]

Acepto y creo un nuevo filtro:

[IMG]http://img63.imageshack.us/img63/452/pantallazo4e.png[/IMG]

[IMG]http://img97.imageshack.us/img97/3153/pantallazo5k.png[/IMG]

**NOTA,** por alguna razón no pude elegir los pixels a mano, solo puedo mover la barrita de abajo y acomodarlo a la resolución óptima del telefono.

**Resoluciones óptimas:**

Nokia 5530, 5535, 5800, N97, N97mini, X6, Otros Symbian S60v5 - 640x360
Nokia N95, N96, Otros S60v3 - 320x240
LG Cookie - 400x240

Por ultimo configuro el codec de audio(pero esto va a gusto, dejo mi ejemplo)

[img]http://img96.imageshack.us/img96/9385/pantallazo6.png[/img]

Una vez terminado esto te vas a **Archivo** -> **Guardar** -> **Guardar video...** y pones el nombre del archivo con un "**.mp4**" al final.

Consejo final: Dependiendo el largo del video y la fuente(mas si es en alta definicion), te recomiendo que guardes y ta vayas a hacer un te, cafe o mates, pro que tarda algun tiempo!!!!(ojo yo por que tengo un monocore, no se con un dual, tri o quad core como andara!!!)

---

### Post by ponchomx on 2010-01-15
Gracias a mi también me ha sido de utilidad.

Salu2

---

### Post by leosr on 2010-01-15
A mi también me resultó util. En mi caso tengo un LG Cookie, hay que configurar la resolución en 400x240 y el audio 44100.

Saludos.

---

### Post by z37a on 2010-01-15
Viendo algunos ejmplos voy a agregar una tablita con algunasresolucones optimas para diferentes telefonos(y en caso necesrios los codecs tambie!!)

---

### Post by z37a on 2010-02-04
Perdon pro doble post, pero me parecio importante acotar algo:

Gente, NO UTILIZEN EL PAQUETE AVIDEMUX DE GETDEB. Lo aclaro en mayusculas pro que agregue hace poco getdeb y ahora que se me actualizo el avidemox no puedo pasar mas videos, fallan al reproducirse en el celular, no se si sera que quedo alguna opción habilitada por defecto o que, pero no funcionan, así que les recomiendo no usar avidemux de getdeb!!!!

---

