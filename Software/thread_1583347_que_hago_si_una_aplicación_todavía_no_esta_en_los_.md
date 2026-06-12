---
title: "que hago si una aplicación todavía no esta en los repositorios para mi distribucion"
date: 2010-09-27
forum: Software
---

### Post by semental on 2010-09-27
antes que nada les advierto soy un usuario novato de ubuntu, así que perdonen la ignorancia y cualquier error de interpretación y de conceptos

acabo de pasarme de ubuntu 10.04 a la beta del 10.10, y me pasa algo que también me paso cuando actualice de karmic a lucid

los orígenes de terceros, no generan repositorios para determinada distribución al mismo tiempo que lo hacen los oficiales, tardando a veces mucho mas (ej. me paso con openoffice con lucid)

Esto me genera que cuando quiero actualizar y tengo como origen de software el emesene para poner por ejemplo, siendo la sintaxis la siguiente:

"deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) maverick main"

me da error 404


Cual es la solución temporaria para esto?

-cambiarle el nombre de la distro por la anterior?

ejemplo, emesene quedaría asi (aunque tenga maverik 10.10)

"deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) lucid main"

me suena que si hago esto si voy a seguir recibiendo actualizaciones, pero no se va a cambiar automáticamente cuando se hagan repositorios de maverik, por ende voy a estar condenado a siempre recibir los de lucid

-poner las dos lineas?:

"deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) lucid main"
"deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) maverick main"

con esto estaría cubierto por ahora y en un futuro?



Repito, disculpen mi ignorancia en el tema, cualquier corrección y ayuda son bien recibidas


espero sus respuestas

desde ya muchas gracias

---

### Post by guillermolisi on 2010-09-27
Las versiones que aun no han alcanzado un aceptable estado de desarrollo como para que sean utilizadas masivamente, caso de las llamadas alpha, beta y release candidate, no se aconsejan para el uso diario, solo para probarlas, relevar problemas e informarlos para que sean solucionados antes de que llegue la version final.

En tu caso estas utilizando la 10.10 que tiene fecha de lanzamiento como version final recien para el 10/10/2010, o sea que estas utilizando una version beta que se modifica diariamente y para la cual muchos programas accesorios, caso emesene, pueden no estar todavia a la altura de las circunstancias (porque aun quedan detalles para definir como definitivos), por eso es que aun no los encontraras en los repositorios "normales" de Ubuntu.

Las versiones en desarrollo, como la 10.10, utilizan un juego aparte de repositorios como una forma de evitar que se "mezcle la hacienda" :)

Una vez lanzada la ultima version estable, cuando procedes a la actualizacion via Internet y como parte de este proceso, los repositorios de adecuaran conviertiendose en los normales vigentes. Tambien con el paso de las primeras semanas iran apareciendo nuevas versiones de aquellos programas que fueron adecuados a ultimo momento y no llegaron en fecha para su lanzamiento definitivo.

---

