---
title: "¿Como corroborar permisos del usuario sobre archivos?"
date: 2009-06-29
forum: Software
---

### Post by clasificado on 2009-06-29
El otro día configurando los permisos de la carpeta /usr/src para que un cronjob corriendo en su propio usuario realice cierta tarea me cayó la duda: **¿Como puedo estar seguro de que va a poder escribir?**

La teoria la entendí: Hago un grupo, le asigno el grupo al usuario, le asigno el grupo a la carpeta (--recursive) le doy chmod g+w (--recursive de nuevo) y a otra cosa.

Pero... ¿como estar seguro?

Se me ocurrió el comando touch, pero modifica la hora de acceso, y no veo en las man page algo como para que no lo haga.

Les cuento la lógica de mi inquietud: soy programador, no me gusta adivinar, me gustan los valores binarios. Quisiera una herramienta que me diga "SI podes leer" "NO podes escribir" y desde la perspectiva de un usuario, no me gusta el resultado del LS, no es concluyente

Buscando y buscando, encontré un muchacho que lo implementó en C: 
[8.2 access: Testing File Permissions]("http://www.informit.com/articles/article.aspx?p=23618&seqNum=3")

Pero se me ocurre que ya tiene que haber una herramienta gnu que haga algo así.

¿A alguno se le ocurre?

clasificado

---

### Post by pablo.s on 2009-06-29
No entiendo por qué decís
que el resultado de ls no es
concluyente. Los permisos
no son loteria.

---

### Post by clasificado on 2009-06-29
me ha pasado tener errores de typo en los nombres de los grupos, por ejemplo

o de asignar permisos a "others" dando por sentado que el usuario caia en esa rama de permisos cuando en realidad SI estaba en el grupo

no digo que sea lotería, solo que son unas cuantas variables y tengo que andar deduciendo cual será el resultado final, cuando me gustaría algo mas directo que me permita reducir el margen de error humano: ¿puede escribir? /si|no/. ¿se entiende?

clasificado

---

### Post by pablo.s on 2009-06-29
Si, se entiende.
No conozco ninguna herramienta
que te ayude. A lo mejor algún
script en bash que puedas armar.
Por lo que veo del código en C
se podría pasar a bash de alguna
manera.

---

