---
title: "Problema con Synaptic"
date: 2009-04-25
forum: Software
---

### Post by JUTGtgRB7z on 2009-04-25
Hola. Ayer instalé la versión 9.04 y ahora  a la hora de instalar desde Synaptic todas las apps que uso noté que faltan muchas. Por ej: el compizconfig, emerald, ubuntu-restricted-extras. La pregunta es si esto es un problema en mi PC o les pasa a todos.:confused: Desde ya gracias

---

### Post by guillermolisi on 2009-04-25
> **pmzerdan said:**
> Hola. Ayer instalé la versión 9.04 y ahora  a la hora de instalar desde Synaptic todas las apps que uso noté que faltan muchas. Por ej: el compizconfig, emerald, ubuntu-restricted-extras. La pregunta es si esto es un problema en mi PC o les pasa a todos.:confused: Desde ya gracias
Faltan porque te dice que no estan instaladas o no figuran en la lista de paquetes porque algunos repositorios no estan incluidos ?

---

### Post by JUTGtgRB7z on 2009-04-25
> **guillermolisi said:**
> Faltan porque te dice que no estan instaladas o no figuran en la lista de paquetes porque algunos repositorios no estan incluidos ?

No me aparecen en la lista de repositorios.:(

---

### Post by guillermolisi on 2009-04-25
> **pmzerdan said:**
> No me aparecen en la lista de repositorios.:(
O sea que podrias resolver el problema agregando los que te faltan.
Si esto es asi, con ver que repositorios tenias habilitados antes (posiblemente ahora figuren comentados) y copiarlos modificando Intrepid por Jaunty deberias tener acceso nuevamente a los paquetes que te faltan.

Podes usar el administrador de repositorios (Software Sources), el mismo Synaptic o un editor que sea de tu comodidad (vim, nano, gedit, etc.) para trabajar el archivo /etc/apt/sources.list

---

### Post by Hei Ku on 2009-04-25
Tenes todos los repositorios habilitados?

---

### Post by JUTGtgRB7z on 2009-04-25
> **Hei Ku said:**
> Tenes todos los repositorios habilitados?

[SIZE="4"]No se muy bien a que te refieres así que te contesto con una imagen.[/SIZE]

[IMG]http://www.23hq.com/pmzerdan/photo/4243970/original[/IMG]

---

### Post by guillermolisi on 2009-04-25
> **pmzerdan said:**
> [SIZE=4]No se muy bien a que te refieres así que te contesto con una imagen.[/SIZE]


Hasta ahi esta todo lo que tiene que estar.
Fijate que tenes en la solapa Software de Terceros.

Tambien fijate si los paquetes que decis te faltan figuran como instalados o no en Synaptic.

---

### Post by JUTGtgRB7z on 2009-04-25
> **guillermolisi said:**
> Hasta ahi esta todo lo que tiene que estar.
Fijate que tenes en la solapa Software de Terceros.

Tambien fijate si los paquetes que decis te faltan figuran como instalados o no en Synaptic.

Esto es lo que tengo en software de terceros:

[IMG]http://www.23hq.com/pmzerdan/photo/4244242/original[/IMG]

En cuanto a que aparezcan en Synaptic, no. No aparecen, ni instalados ni no instalados.Lo que sí encontré en "Añadir o quitar programas" es el cssm (CompizConfig). Pero emerald no. :S

---

### Post by staar on 2009-04-25
pregunta, estás usando la búsqueda rápida o el botón buscar? mejor usá el botón, me ha pasado que la búsqueda rápida tampoco me encontraba algunos paquetes (supongo que buscará entre los que están listados en ese momento, no sé)...

otra, recargaste los repositorios despues de activarlos?...

de última proba con apt-get o aptitude, desde la terminal ```
sudo aptitude install ubuntu-restricted-extras emerald
```

PD: ccsm no lo vas a encontrar si lo buscás así (ya que esa abreviatura no esta ni en el nombre del paquete, ni en su descripción) buscá la palabra compiz, y ahí te va a aparecer, creo que se llama compizconfigsettingsmanager, o con algún guión por ahí en el medio :-P ...

saludos

---

### Post by Apipote on 2009-04-25
Proba en la consola con:

> sudo update-apt-xapian-index

Suele resolver el problema de un bug viejo y desagradable en los indices al usar la busqueda rápida.

Ojala te sirva.

---

### Post by JUTGtgRB7z on 2009-04-26
> **Apipote said:**
> Proba en la consola con:



Suele resolver el problema de un bug viejo y desagradable en los indices al usar la busqueda rápida.

Ojala te sirva.

Esa fue la solución, muchas gracias.:)

---

