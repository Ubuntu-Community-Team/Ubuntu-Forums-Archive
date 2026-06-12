---
title: "Migrar BD Mysql de Win a Ubuntu"
date: 2009-07-10
forum: Software
---

### Post by jacc90220 on 2009-07-10
Hola,
 
Tenemos un BD desarrollada en Mysql, con uno de esos programas triad (como el wamp) y esta bajo windows. Como esta hace casi 2 años funcionando y va muy bien, tenemos ya bastante información.
 
Como soy nuevo en ubuntu y monte un server, queremos migrar la BD y la aplicacion (php y javascript).
 
En windows bastaba con mover la carpeta data (dependiendo el triad q usáramos) y listo, pero en linux sinceramente no tengo idea como hacerlo.
 
Muchas gracias por su apoyo.
 
Slds

---

### Post by guillermolisi on 2009-07-10
> **jacc90220 said:**
> Hola,
 
Tenemos un BD desarrollada en Mysql, con uno de esos programas triad (como el wamp) y esta bajo windows. Como esta hace casi 2 años funcionando y va muy bien, tenemos ya bastante información.
 
Como soy nuevo en ubuntu y monte un server, queremos migrar la BD y la aplicacion (php y javascript).
 
En windows bastaba con mover la carpeta data (dependiendo el triad q usáramos) y listo, pero en linux sinceramente no tengo idea como hacerlo.
 
Muchas gracias por su apoyo.
 
Slds
Si bien el tema principal de tu inquietud esta centralizado en MySQL y no tanto en Ubuntu, mis consejos iniciales, antes de mover un solo bit, son:

Verifiquen que version de MySQL van a usar en Ubuntu y contrasten sus diferencias con la que estan usando en Windows. Dos años sin actualizaciones en MySQL es mucho tiempo y han habido cambios importantes, algunos bien documentados y otros no tanto.

Documenten los requerimientos y la configuracion de MySQL bajo Windows para luego replicar lo mismo bajo Ubuntu. Una diferencia minima en un tipo de datos, en el set de caracteres a usar contra el usado, etc. puede resultar en una migracion insufrible por lo complicada y lo larga.

Luego y considerando que seguramente hay mas de un camino para lograr lo mismo y que tienen todo normalizado, estudiado y bien dispuesto para que no se presenten problemas con el cambio de version/plataforma, realizaria un vuelco de la estructura/esquema de la o las bases/instancias junto con su contenido, tabla por tabla, de forma tal que con lo generado (un archivo conteniendo toda la secuencia SQL necesaria y suficiente para crear la o las bases, asignar correctamente los permisos, crear y generar las tablas, crear usuarios, etc.) puedan recrear en MySQL bajo Ubuntu lo mismo que tienen en Windows.

Si no recuerdo mal (no soy un experto en la materia) creo que con MySQLDump y las opciones adecuadas podes lograr lo que te comento.

Otro tema importante es tener especial cuidado con las versiones de PHP. Entre PHP3 y las siguientes se dieron cambios radicales.

---

### Post by fmsismo on 2009-07-10
Hola, Alvaro subió un tuto de como poner en marcha LAMP (Linux, Apache, MySQL y PHP)

[http://www.sismonda.com.ar/node/161](http://www.sismonda.com.ar/node/161)

Saludos

---

### Post by jacc90220 on 2009-07-10
Muchas gracias por los consejos guillermolisi y fmsismo.
 
Hare la verificación y luego les cuento.
 
Slds

---

