---
title: "¿Que rc utiliza Ubuntu 9.04?"
date: 2009-09-23
forum: Software
---

### Post by emiliano_raso on 2009-09-23
Tengo Ubuntu 9.04 y con un amigo estabamos urgando en los **rc**.
Buscamos información y encontramos que Ubuntu trabaja con **rc1.d**, sin embargo, la mayoria de las dependencias de **rc1.d** son K y muy pocos son S.
Seguimos revisando y el **rc2.d** tenia todas dependencias de start, pero al modificar/agregar, nada sucedió.

Que run level usa Ubuntu?


PD: Si este thread ya estaba en el foro, la busqueda no me lo tiró :-P Sepan disculpar.

---

### Post by pablo.s on 2009-09-23
Antes de "urgar" en los .rc
tendrías que leer los links
que puse en [este post]("http://ubuntuforums.org/showpost.php?p=7887236&postcount=6").
**Consejo de amigo:** no toquen
nada ni le cambien ninguna
letra antes de saberse esta
información de memoria.

---

### Post by emiliano_raso on 2009-09-23
> **pablo.s said:**
> Antes de "urgar" en los .rc
tendrías que leer los links
que puse en [este post]("http://ubuntuforums.org/showpost.php?p=7887236&postcount=6").
**Consejo de amigo:** no toquen
nada ni le cambien ninguna
letra antes de saberse esta
información de memoria.

ADVERTENCIA: Este artículo está desactualizado en gran parte, ya que, desde la versión 6.10, Ubuntu utiliza Upstart.

---

### Post by pablo.s on 2009-09-23
Upstart reemplaza a init,
pero los runlevels hasta el
dia de hoy se siguen usando.

---

### Post by emiliano_raso on 2009-09-23
Ok... gracias por la data.. ahora probamos...
Tenemos una maquina con Debian Lenny y la mia con Ubuntu y no coincide ni a patadas :-P

---

### Post by pablo.s on 2009-09-23
¿Que cosa no coincide?

---

### Post by juancarlospaco on 2009-09-23
Los runlevels estan pero en modo compatibilidad, 
no son realmente lo que son en otros sistemas, 
algunos runlevels son la misma cosa en realidad,
el Upstart creado por Ubuntu se basa en iniciar el sistema por eventos,
el viejo sistema por scripts secuenciales no basados en eventos,
tenia el inconveniente que a veces al iniciar el sistema se reinicializaba un mismo dispocitivo demasiadas veces, 
cuando en realidad solo se necesita inicializarlo una vez;
o cuando se insertaba un pendrive mientras se esta booteando hacia lio,
o cosas asi, por eso se cambio por Upstart que es mejor en ese sentido.

Lo usa Fedora, a futuro Debian cambiara a Upstart tambien, pero aun no han cambiado.
:)

---

