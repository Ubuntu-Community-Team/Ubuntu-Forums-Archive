---
title: "Tamaño de hoja personal - CUPS"
date: 2009-10-07
forum: Software
---

### Post by z37a on 2009-10-07
Gente, hoy me estuve peleando con el CUPS un rato(para poder administrarlo remoto, muchas trabas por seguridad, pero bue, solucionado, espero no haber dejado un gruyer con la seguridad jeje), lo que me quede es con una gran duda en algo, yo tengo el CUPS funcionando en un server al cual hay conectada una impresora Laserjet 1028 de HP, lo que quiero es saber como puedo hacer para poder configurarle un tipo de hoja personalizado(un tamaño personalizado), ya que lo que quiero es poder imprimir de vez en cuando sobres de CD. Alguno sabe como podría hacerlo?

---

### Post by faktorqm on 2009-10-08
Me costo trabajo encontrarlo... buena pregunta!

Si tenes el servidor levantado (como es mi caso) en la ayuda aparece eso. En mi caso la direccion es

[https://fileserverii:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=](https://fileserverii:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=)

vos tendrias que poner (si no usas https)

```
http://nombre_de_tu_server_o_ip:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=
```

Y busca el titulo que dice "custom options" que ahi te dice como agregar un custom page size para tu impresora. La verdad, pense que era mas facil... Salu2!

---

### Post by z37a on 2009-10-08
> **faktorqm said:**
> Me costo trabajo encontrarlo... buena pregunta!

Si tenes el servidor levantado (como es mi caso) en la ayuda aparece eso. En mi caso la direccion es

[https://fileserverii:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=](https://fileserverii:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=)

vos tendrias que poner (si no usas https)

```
http://nombre_de_tu_server_o_ip:631/help/spec-ppd.html?TOPIC=Specifications&QUERY=
```

Y busca el titulo que dice "custom options" que ahi te dice como agregar un custom page size para tu impresora. La verdad, pense que era mas facil... Salu2!

Es bastante complicado de verdad!!!! gracias por la data, voy a ver que onda eso!!! Yo me volví loco buscando en google y busque en el help pero no di nunca con esto, solo leí que es un problema que también tiene las gui que no tiene dicha opción, la verdad que es muy util eso, no se como todavía no salio nada para facilitarlo.

---

