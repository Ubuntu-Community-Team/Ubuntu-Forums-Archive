---
title: "Desaparece texto de programas y menúes"
date: 2009-03-28
forum: Software
---

### Post by Andyvec on 2009-03-28
Hola a todos nuevamente.

Tengo un inconveniente, los textos de los menúes de algunos programas no se visualizan. Entre ellos OpenOffice 3 o por ejemplo la configuración de Wine (los únicos programas que instalé, la distro 8.10 esta recién instalada) en ambos casos cuando paso el mouse por arriba de una opción llego a ver el destello con los textos y están en español, pero no permaneces, agrego una captura para que se den cuenta:

[[IMG]http://img291.imageshack.us/img291/2084/captura.png[/IMG]](http://img291.imageshack.us/my.php?image=captura.png)

Revisé el Soporte para Idiomas e instalé el Castellano que no estaba, pero el problema persiste.

---

### Post by pablo.s on 2009-03-28
Hola: para el problema de WINE te recomiendo instalar las fuentes de
MS. En una terminal escribi esto:

sudo apt-get install msttcorefonts

y con esto es muy probable que el problema de WINE se solucione.

---

### Post by Andyvec on 2009-03-28
Gracias por tu respuesta.

Ya tengo instaladas estas Fuentes, fue lo primero que pensé. La verdad es que no se de que se trate, pero creo que es el mismo problema, algo de Ubuntu esta andando mal, por ahora son las únicas dos aplicaciones con esto.

Como se ve en la captura, los textos de los menúes no aparecen, en su lugar un "_".

Saludos, continúo buscando una solución, estoy atento a cualquier idea o posible solución.

---

### Post by Hei Ku on 2009-03-28
Desactivaste Compiz?

---

### Post by Andyvec on 2009-03-28
Si, probé desactivas Compiz.

Encontré una solución parcial para el caso de OpenOffice 3, tuve que ir Sistema > Preferencias > Apariencia y en la pestaña de tipografías elegir la opción de Suavizado de Sub-píxel (LCD). Ahora se ven todos los textos y menúes en OpenOffice.

Sin embargo el problema continúa en otras aplicaciones como los menúes de Wine, aMSN y algunos programitas que estoy instalando.

Según leí por algún lado puede tener que ver con drivers de nvidia (uso una placa GeForce 2 MX400 64MB que es un poco complicada) pero que esta vez pude instalar correctamente con aceleración 3D y todo los chiches del driver original actualizado. La placa me trajo problemas en otras instalaciones Linux y Ubuntu, no me gustaría cambiar los drivers porque por primera vez andan bien, sin embargo si no puedo ver los menúes...

Bueno, sigo en la búsqueda de la solución.

---

### Post by euzkoarima on 2009-03-31
Tengo idea que tuve el mismo problema con el openOffice cuando ibamos por 7.10 o 7.04 y si la memoria no me falla el motivo es que estaba usando un tema "no compatible" con el openOffice. Me refiero obviamente a los temas que instalas en Sistema -> Preferencias -> Apariencia.

Seguro que cuando tuve el problema no tenía ni siquiera instalado compiz (o como se llamara en esa época), o sea era un tema gtk.

Proba de poner Human (el que viene por defecto) y fijate si se arregla o no.

Saludos,
Eduardo

---

### Post by Andyvec on 2009-04-02
Gracias por tu respuesta.

El problema con OpenOffice ya está solucionado. Era un tema de suavizado de fuentes (tenía que elegir por subpíxel para LCD)

El problema lo sigo teniendo en todas las demás aplicaciones que instalé (la más imporatante para mi WINE).

Saludos

---

