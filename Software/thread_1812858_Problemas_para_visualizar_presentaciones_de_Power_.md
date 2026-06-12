---
title: "Problemas para visualizar presentaciones de Power Point"
date: 2011-07-26
forum: Software
---

### Post by biale on 2011-07-26
Mi hija esta recibiendo presentaciones de Power Point (ppt) de la facultad que no tienen nada raro, solo textos sobre un fondo neutro. El problema es que con Open Office Impress, los textos a veces “se caen” de la pantalla y resultan imposibles de leer. 

Hasta ahora, lo único que funciona es hacer trabajar al Impress en modo edición, aunque no los pueda editar y salvar, pero al menos los puede desplegar completos.

Va entonces mi primer consulta (tonta): es posible con algun flag o atajo de teclado hacer que Impress los arranque en modo edición, en lugar de pasar directamente al modo de presentación, como sucedía con hardy y anteriores?  O bien cancele el modo de presentación y pase al modo edición?

Si la idea es representarlos bien, parece no ser muy fácil. Ya probé con la última versión de Libre Office y no funcionó. También los viewers Office 2007/ 2010 en Lucid bajo wine sin resultados. Incluso con un conversor web ppt a pdf y peor todavía.

Ni siquiera en una PC que tiene WXP y Office 2000 renderizan bien. Tampoco instalando sobre WXP virtualizado los viewers (!?) O sea que el problema pasaría tanto por la versión de Win como por la del Office que usaron para crearlos. Que combinación serviría?

Va entonces mi segunda consulta: han tenido el mismo problema? Se le ocurre algo mas?

Muchas gracias de antemano...

---

### Post by guillermolisi on 2011-07-26
He visto presentaciones que solamente se ven y funcionan bien cuando se las reproduce con la misma version de PPoint con la que fueron realizadas, en general Office 2007 en adelante.

Cuando las abro con Impress algun detalle siempre se escapa, tal como decis vos que pasa con el posicionamiento del texto, con los efectos, con sonidos/musica, etc.

Conclusion, lo ideal seria que las presentaciones se soliciten en formato ODF (si, ya se que es como pedir peras al olmo pero alguna vez tenemos que empezar). Con eso se terminan las incompatibilidades, inclusive para versiones anteriores de MS Office. Y la excusa "Pero no tengo Open/Libre Office" no sirve porque existen versiones para Windows que no requieren mas que ser instaladas.

No se puede hacer una tortilla sin romper algunos huevos. :)

---

### Post by biale on 2011-07-27
Guillermo, por supuesto que estoy de acuerdo con vos. Incluso si las presentaciones las hubieran entregado en formato pdf no habría problemas.

En este caso pareciera que problema viene por la sustitución de fonts. La vuelta que encontre fue simplemente renombrar los archivos desde .pps a .ppt y de esa manera OO los abre en modo edición y no en modo presentación. Con eso por lo menos se logra leer lo escrito

Otros arman un comando personalizado "ooimpress -n filename" que hace lo mismo.

(No encuentro un botón "solved")

---

### Post by guillermolisi on 2011-07-28
Adjunto imagen de ejemplo para marcar como Solved los threads.

---

