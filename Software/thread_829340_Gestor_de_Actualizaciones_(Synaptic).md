---
title: "Gestor de Actualizaciones (Synaptic)"
date: 2008-06-14
forum: Software
---

### Post by Elrengo on 2008-06-14
Soy nuevo en esto, solo un par de meses. y mi consulta es simple.

Es recomendable instalar TODAS las actualizaciones q aparecen en el gestor de descargas de SYNAPTIC??

por supuesto solo instalo las de seguridad y la de los programas q utilizo, pero es recomendable todas??

---

### Post by marianom on 2008-06-14
El gestor solo te avisa de las actualizaciones que se corresponden con los programas que tenés instalados (voluntariamente o porque vienen por defecto) ya sean de seguridad o ajustes de bugs varios. Lo recomendable es instalar todas (en muy pocos casos una actualización pueden romper algo que ya tengas y debería ser siempre una excepción). Si ves una que se corresponda con un programa crítico para vos mirá el detalle de aquello que se corrige para que entiendas como te afecta y consulta si te genera dudas.

---

### Post by pol666 on 2008-06-14
a mi las actualizaciones de Kernel ej: Linux-headers, Linux Image, Linux Kernel etc. etc.  me arruinan la PC


asi que no las hago.

---

### Post by Hei Ku on 2008-06-14
vos tenes drivers propietarios, por eso las actualizaciones de kernel te arruinan la pc. Desgraciadamente, los drivers propietarios no se actualizan bien en esos casos.
Pero, las actualizaciones son necesarias por temas de seguridad en muchos casos. Es cuestion de elección.

---

### Post by Kantier on 2008-06-14
> **Elrengo said:**
> Soy nuevo en esto, solo un par de meses. y mi consulta es simple.

Es recomendable instalar TODAS las actualizaciones q aparecen en el gestor de descargas de SYNAPTIC??

por supuesto solo instalo las de seguridad y la de los programas q utilizo, pero es recomendable todas??
Ante tu duda, una pregunta debes hacerte:

¿Instalaste algo en el sistema por afuera de synaptic (apt-get en realidad, pero asumo que no sabés lo que hay abajo de synaptic) o de los archivos .deb?

Si instalaste algo desde un .tar.gz (hablo de cosas como drivers de video), entonces you're [SOL]("http://en.wiktionary.org/wiki/SOL")(#4)

---

### Post by santiagoward2000 on 2008-06-14
> **Kantier said:**
> Si instalaste algo desde un .tar.gz (hablo de cosas como drivers de video), entonces you're [SOL]("http://en.wiktionary.org/wiki/SOL")(#4)

**SOL** como **speed of light**, no?? ;)

---

### Post by oktubrer on 2008-06-14
Yo tengo los drivers de nvidia propietarios, hago todas las actualizaciones incluyendo las del kernel, y nunca tuve problemas.
La única excepción es con el open office, con el cual todavía estoy luchando, pero fue después que instalé y desinstalé el xubuntu-desktop, así que no es un problema en sí de las actualizaciones.

---

### Post by atari130xe on 2008-06-14
Ya que estamos.... así como quien no quiere la cosa... si en "updates" tildo proposal y backports afecta en algo al sistema? o sea me cambia mucho el panorama o solo ocupo más espacio en el HD? o pongo en peligro la estabilidad del OS. Resulta que encont&#341;e en proposal el update de EnvyNG con la última versión del driver de Nvidia 169... que al tener un par de bugs, me hizo las cosas un poco más dificiles (cierre del nevegador, cuelgues con programas, la no posibilidad de abrir ciertos sitios, etc.) o sea esa "nueva" versión instala el 173.14.05 (el último).

POD: I must be a S.O.L. cause I can compile my own software :lolflag: (aunque a veces haga preguntontas) jejeje

---

### Post by pol666 on 2008-06-15
lo mio es con el sonido, y el Xorg
Mueren despues de actualizar kernel asi que no las hago. No hay formas de anularlas definitivamente?

osea cancelarlas por siempre?

---

### Post by santiagoward2000 on 2008-06-15
> **pol666 said:**
> lo mio es con el sonido, y el Xorg
Mueren despues de actualizar kernel asi que no las hago. No hay formas de anularlas definitivamente?

osea cancelarlas por siempre?

Hola!
Bue, si no queda otra que no actualizar, podes seleccionar el paquete en Synaptic, abrir el menu **Package** y tildar la opcion **Lock version**.
Saludos!

---

