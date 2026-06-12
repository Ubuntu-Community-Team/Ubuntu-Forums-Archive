---
title: "No puedo instalar Chrome en Kubuntu 11.04"
date: 2011-08-22
forum: Software
---

### Post by aledruetta on 2011-08-22
Hola Comunidad!

No sé por qué, pero no puedo instalar Chrome en Kubuntu 11.04.

Probé con el .deb estable, probé agregando los repositorios estables.

Les dejo un pantallazo del error que tira. Aclaro que aparece un origen alternativo, porque probé con otros repositorios para ver si ese era el problema. Con los repositorios de instalación o con el .deb, sucede lo mismo.

Alguna sugerencia?

---

### Post by guillermolisi on 2011-08-22
Proba de nuevo pero cambiado el origen de los mirrors. Pareceria que ese paquete que origina el error esta en el indice del repositorio brasilero pero no existe fisicamente.

---

### Post by aledruetta on 2011-08-22
> **guillermolisi said:**
> Proba de nuevo pero cambiado el origen de los mirrors. Pareceria que ese paquete que origina el error esta en el indice del repositorio brasilero pero no existe fisicamente.

Hola Guillermo,

Ya había cambiado los mirrors oficiales para brasil por otros. Ahora probé con mirrors de Argentina. Y en todos los casos el mensaje de error es el mismo.

Debe ser alguna otra cosa...

---

### Post by aledruetta on 2011-08-22
Existe alguna forma de restaurar los repositorios originales, como estaban al momento de la instalación, por las dudas que sea algo que se desbarajustó ahí?

---

### Post by guillermolisi on 2011-08-22
Yo uso los centrales (archive.ubuntu.com/...) y nunca tuve mas problemas de inconsistencias. De hecho como uso Chromium tengo esa libreria y su dependencia instaladas sin inconvenientes.

Para cambiar de mirror podes usar el Gestor de Actualizaciones - Preferencias o Synaptic (en ambos casos te lleva al mismo lugar) y elegis de que lugar queres usar el mirror (es mas rapido que editar el archivo /etc/apt/sources.list)

---

### Post by aledruetta on 2011-08-22
> **guillermolisi said:**
> Yo uso los centrales (archive.ubuntu.com/...) y nunca tuve mas problemas de inconsistencias. De hecho como uso Chromium tengo esa libreria y su dependencia instaladas sin inconvenientes.

Para cambiar de mirror podes usar el Gestor de Actualizaciones - Preferencias o Synaptic (en ambos casos te lleva al mismo lugar) y elegis de que lugar queres usar el mirror (es mas rapido que editar el archivo /etc/apt/sources.list)

Yo también estoy usando Chromium, por lo que me resulta más raro que no permita instalar Chrome y me dé ese mensaje de error. Los mirrors ya los cambié varias veces, ese no es el problema, el error se repite para cualquiera de ellos. 

Pregunto si hay alguna forma de dejar el sources.list como estaba al momento de la instalación, para ver si eso no resuelve.

---

### Post by aledruetta on 2011-08-22
Ah, y la decisión por los mirrors de brasil en lugar del servidor principal es que en el servidor principal la velocidad es 2k por segundo, mientras en el servidor de la USP de Brasil es de 455k por segundo. Pero independientemente de eso, en los dos da el mismo error.

---

### Post by guillermolisi on 2011-08-22
> **aledruetta said:**
> 
Pregunto si hay alguna forma de dejar el sources.list como estaba al momento de la instalación, para ver si eso no resuelve.

Si, si recordas que pais elegiste al momento de la instalacion es posible volver a elegir algun mirror que se corresponda con el.
Generalmente se establece uno de los mirrors como principal, para el caso de que el pais posea mas de uno, pero esa situacion puede cambiar si sale de servicio, el enlace es defectuoso o esta desactualizado.

Para mas consultas sobre mirrors ir a [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

ahi te muestra como esta cada uno de los casi 400 en el mundo.

---

