---
title: "Indicación de fallas en disco rígido"
date: 2009-12-27
forum: Software
---

### Post by mano negra on 2009-12-27
Buenas,
   Disculpen que no cerré el anterior Thread sobre como configurar las particiones en Ubuntu. Me han pasado un par de cosas con el 9.10 en estos días.
    Cuando instalo la 9.10 me sale un alerta indicando que el disco rígido está fallando. Además de que llegó a colgarse, y a veces andaba muy lento. Hasta hace un rato estaba convencido que mi disco rígido realmente estaba roto, pero leyendo en foros al parecer es un bug del sistema. ¿A alguien le pasó o le pasa lo mismo? Si es así ¿alguien encontró una solución?
    Les cuento que con el 8.10 no tuve problema alguno. Y estuve pensando en instalar el 9.04, como para tener algo más estable.
Salud!

---

### Post by z37a on 2009-12-27
> **mano negra said:**
> Buenas,
   Disculpen que no cerré el anterior Thread sobre como configurar las particiones en Ubuntu. Me han pasado un par de cosas con el 9.10 en estos días.
    Cuando instalo la 9.10 me sale un alerta indicando que el disco rígido está fallando. Además de que llegó a colgarse, y a veces andaba muy lento. Hasta hace un rato estaba convencido que mi disco rígido realmente estaba roto, pero leyendo en foros al parecer es un bug del sistema. ¿A alguien le pasó o le pasa lo mismo? Si es así ¿alguien encontró una solución?
    Les cuento que con el 8.10 no tuve problema alguno. Y estuve pensando en instalar el 9.04, como para tener algo más estable.
Salud!

No se pero yo gracias a 9.10 detecte que realmente tenia 2 discos con fallas en mi casa, uno sigo usandolo ya que tenia algunos secotres dañados y no tengo nada importante ahi, el otro bueno me detecto unos cuantos y lo jubile, pero con otra herraienta me di cuenta que era verdad y que ambos tenian sectores dañados.

---

### Post by guillermolisi on 2009-12-27
> **z37a said:**
> No se pero yo gracias a 9.10 detecte que realmente tenia 2 discos con fallas en mi casa, uno sigo usandolo ya que tenia algunos secotres dañados y no tengo nada importante ahi, el otro bueno me detecto unos cuantos y lo jubile, pero con otra herraienta me di cuenta que era verdad y que ambos tenian sectores dañados.
Que otra herramienta ? Smartmon tools ? fsck ?

---

### Post by z37a on 2009-12-27
> **guillermolisi said:**
> Que otra herramienta ? Smartmon tools ? fsck ?

Cualquiera que lea el smart, en este caso en uno de los discos le use la herramienta del fabricante(Maxtor) y de paso le hize un formato a bajo nivel.

---

### Post by luks911 on 2009-12-27
> **mano negra said:**
> Buenas,
   Disculpen que no cerré el anterior Thread sobre como configurar las particiones en Ubuntu. Me han pasado un par de cosas con el 9.10 en estos días.
    Cuando instalo la 9.10 me sale un alerta indicando que el disco rígido está fallando. Además de que llegó a colgarse, y a veces andaba muy lento. Hasta hace un rato estaba convencido que mi disco rígido realmente estaba roto, pero leyendo en foros al parecer es un bug del sistema. ¿A alguien le pasó o le pasa lo mismo? Si es así ¿alguien encontró una solución?
    Les cuento que con el 8.10 no tuve problema alguno. Y estuve pensando en instalar el 9.04, como para tener algo más estable.
Salud!

A mí me pasó. Ni bien ejecuté 9.10 como live me dijo que mi disco tenía muchos sectores defectuosos. El disco era nuevo, así que se lo atribuí al bug[0]. La "solución" temporal, hasta que se solucione el bug, es desactivar la alarma del controlador de discos. Vas a Sistema > Administración > Utilidad de discos. Luego clickeás en el link que dice "Más información" debajo de tu disco y en el siguiente cuadro de diálogo tildás la casilla de "No avisarme si el disco está fallando". Claro que eso es lo que va a hacer: no avisarte. Pero al menos no molesta el aviso, en este caso, innecesario.

[0] [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by guillermolisi on 2009-12-27
> **mano negra said:**
> Está claro que tengo que cambiar el disco. No me paran de surgir dudas...Estas son mis consultas:
- ¿Ubuntu soporta sata 2? ¿O más seguro sata?
- Tengo un core 2 duo 6500, no hay problema si instalo el 9.04 de 64 bits? ¿o voy a lo seguro y sigo con 32 bits?

Dudas que me surgen luego de un par de horas por google. Sepan entender, estudio mecánica...
Salud!
Si el tema original de este thread esta resuelto y no te quedan dudas, entonces lo damos por solucionado.

Si tenes otros temas para consultar, como los que mencionaste, entonces abri un thread por cada uno asi trabajamos especificamente sobre cada uno (y mantenemos ordenado el foro).

Las dos preguntas generaron dos threads en la seccion Hardware.

---

### Post by mano negra on 2009-12-27
> **luks911 said:**
> A mí me pasó. Ni bien ejecuté 9.10 como live me dijo que mi disco tenía muchos sectores defectuosos. El disco era nuevo, así que se lo atribuí al bug[0]. La "solución" temporal, hasta que se solucione el bug, es desactivar la alarma del controlador de discos. Vas a Sistema > Administración > Utilidad de discos. Luego clickeás en el link que dice "Más información" debajo de tu disco y en el siguiente cuadro de diálogo tildás la casilla de "No avisarme si el disco está fallando". Claro que eso es lo que va a hacer: no avisarte. Pero al menos no molesta el aviso, en este caso, innecesario.

[0] [https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Gracias por la data!! Me había olvidado de ver tu respuesta
Salud!

---

