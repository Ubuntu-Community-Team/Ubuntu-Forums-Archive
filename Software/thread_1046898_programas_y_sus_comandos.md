---
title: "programas y sus comandos"
date: 2009-01-21
forum: Software
---

### Post by tsueseres on 2009-01-21
hay alguna manera de porder saber cual es el comando para la ejecucion de en programa

porcierto porque aparecen que unos mensajes fueron movidos?

---

### Post by sergiom99 on 2009-01-21
podes fijarte en el acceso directo que comando usa para ejecutarlo, entrando en las propiedades.

Los mensajes los movieron los moderadores para ponerlos en el subforo correspondiente.

---

### Post by tsueseres on 2009-01-22
> **sergiom99 said:**
> podes fijarte en el acceso directo que comando usa para ejecutarlo, entrando en las propiedades.

Los mensajes los movieron los moderadores para ponerlos en el subforo correspondiente.

y si no hay acceso directo?

---

### Post by Air23 on 2009-01-22
> **tsueseres said:**
> y si no hay acceso directo?

En este tema del foro general tenes varias maneras de obtener los nombres que buscas:

[http://ubuntuforums.org/showthread.php?p=6551006](http://ubuntuforums.org/showthread.php?p=6551006)

La que me parecio mas sencilla es esta (en una terminal):

```
man -k keyword
```

Por ejemplo, si como palabra clave pongo "office" obtengo:
```
juan@HAL9000:~$ man -k office
oocalc (1)           - OpenOffice.org office suite
oodraw (1)           - OpenOffice.org office suite
ooffice (1)          - OpenOffice.org office suite
oofromtemplate (1)   - OpenOffice.org office suite
ooimpress (1)        - OpenOffice.org office suite
oomath (1)           - OpenOffice.org office suite
ooweb (1)            - OpenOffice.org office suite
oowriter (1)         - OpenOffice.org office suite
openoffice (1)       - OpenOffice.org office suite
unopkg (1)           - OpenOffice.org Extension Manager
update-openoffice-dicts (8) - rebuild dictionary.lst for OpenOffice.org
```

---

### Post by tsueseres on 2009-01-22
> **Air23 said:**
> En este tema del foro general tenes varias maneras de obtener los nombres que buscas:

[http://ubuntuforums.org/showthread.php?p=6551006](http://ubuntuforums.org/showthread.php?p=6551006)

La que me parecio mas sencilla es esta (en una terminal):

```
man -k keyword
```

Por ejemplo, si como palabra clave pongo "office" obtengo:
```
juan@HAL9000:~$ man -k office
oocalc (1)           - OpenOffice.org office suite
oodraw (1)           - OpenOffice.org office suite
ooffice (1)          - OpenOffice.org office suite
oofromtemplate (1)   - OpenOffice.org office suite
ooimpress (1)        - OpenOffice.org office suite
oomath (1)           - OpenOffice.org office suite
ooweb (1)            - OpenOffice.org office suite
oowriter (1)         - OpenOffice.org office suite
openoffice (1)       - OpenOffice.org office suite
unopkg (1)           - OpenOffice.org Extension Manager
update-openoffice-dicts (8) - rebuild dictionary.lst for OpenOffice.org
```

gracias por esta informacion, pero de casualidad no hay algun comando que te muestre los programas o ventanas que estan actualmente corriendo?

---

### Post by Hei Ku on 2009-01-22
el comando top te muestra los programas que estan haciendo uso del procesador

---

### Post by guillermolisi on 2009-01-22
> **Hei Ku said:**
> el comando top te muestra los programas que estan haciendo uso del procesador
Top te los muestra "en vivo" mientras que el comando ps te muestra una salida estatica, una "foto", de lo que esta corriendo en ese momento.

ps tiene cantidad de opciones. Para saber cuales usar mas convenientemente, ingresa en consola 'man ps'. (Suelo usar ps -ef para ver quien esta corriendo qe cosa y que archivos son los que iniciaron el proceso junto con sus parametros).

---

### Post by tsueseres on 2009-01-22
gracias por la informacion

---

