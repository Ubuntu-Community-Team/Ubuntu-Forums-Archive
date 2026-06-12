---
title: "recuperar evolution"
date: 2009-11-17
forum: Software
---

### Post by capcabgue on 2009-11-17
Hola a todos:

He tenido un problema, bueno para resumir, eliminé todos los .* de mi home, pero como quería recuperar los correos hice un 
$ mv .evolution evolution_backup
Una vez reiniciado el pc volví a crear .evolution

El problema que esto en teoría me debiara permitir recuperar las direcciones de correo, los e-mail, calendarios, etc. pero no veo nada, si navego hasta la carpeta creada, efectivamente veo mis cuentas, mis correos (no se donde están los outbox ni los inbox, pero supongo que están ahi).

Mi pregunta es si alguien me puede decir comop hacer para volverlos a recuperar.

Gracias

---

### Post by nopersona on 2009-11-17
Hace tiempo, hace muuuucho tiempo, creo que en feisty, tuve este mismo problema. La cosa es que en Evolution la información se distribuye en distintos directorios y niveles, eso lo comprendí luego de acualizar y sólo guardar .evolution. Para mi desgracia perdí todos los correos. Buscando encontré el orden de los directorios y pude hacer un respaldo para la próxima vez, pero después de eso no me quedaron muchas ganas de seguir usando evolution, menos un cliente de correos por un tiempo. Bueno, ahora en KDE 4 uso kmail, que es mucho más ordenado y sencillo :P

Voy a buscar el orden de los ficheros, a ver si los pillo. Creo recordar que algo se guardaba en .config

P.S.:Moraleja; hacer una partición /home y mantenerla, es lo más sano e inteligente, así lo aprendí yo.

---

### Post by capcabgue on 2009-11-17
> **nopersona said:**
> Voy a buscar el orden de los ficheros, a ver si los pillo. Creo recordar que algo se guardaba en .config 
Gracias, tengo montado sobre linux /home, como se debe, el problema que quería eliminar despues de una año de uso todos los programas que uno va instalando (con deb, tar.gz, synaptic, etc, etc) para dejar todo como nuevo y luego hacer un upgrade.
supuse, que si eliminaba todos los *. algo  quedaba la grafica como nuevo , pero desgraciadamente hubo problemas con los respaldo, tendré que trabajar nuevamente.

Gracias en todo caso por el consejo

---

### Post by moreback on 2009-11-17
¿Ninguno de los dos se fijó en el menú Archivo del Evolution hay una opción llamada "Respaldar ajustes..." que respalda los correos y las configuraciones en un tar.gz?

---

### Post by nopersona on 2009-11-18
> **moreback said:**
> ¿Ninguno de los dos se fijó en el menú Archivo del Evolution hay una opción llamada "Respaldar ajustes..." que respalda los correos y las configuraciones en un tar.gz?

Jojojo :popcorn:  Guarda todito todito, o solo las configuraciones?

---

### Post by Maciett on 2009-11-18
Guarda todo, comprobado.

Saludos

---

### Post by capcabgue on 2009-11-26
Gracias, fue muy tarde y efectivamente no leí el menu.
PLOP:( .

Pero ya se como respaldar la información

---

