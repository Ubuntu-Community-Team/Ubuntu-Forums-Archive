---
title: "wolfeinstein enemy territory"
date: 2009-10-01
forum: Software
---

### Post by lucasgz on 2009-10-01
holas a todos
tengo problemas para jugar online con el enemy territory, me dice que tengo un codigo GUID invalido , nose que sera:confused:
estuve probando algunas soluciones que encontre de google pero sigue igual¿ alguien lo pudo hacer andar?

probe escribir en el juego \pd_cdkeyreg pero tira error

---

### Post by dummy910 on 2009-10-01
Vi varios enlaces aquí que puede ayudarle a hombre:
http://www.google.com/search?hl=en&tbo=1&tbs=rcnt:1&q="pb_cdkeyreg+"+wolfenstein+ubuntu&aq=f&oq=&aqi=

---

### Post by lucasgz on 2009-10-01
los vi, no me soluciono, = se agradece!

---

### Post by lucasgz on 2009-10-02
ya lo solucione tenia que correr el juego como superusuario sudo et

---

### Post by guillermolisi on 2009-10-02
Es normal correr juegos como este como superusuario o hay algun tema de permisos mal asignados ?

Me parece sumamente inseguro.

---

### Post by faktorqm on 2009-10-02
no, mal configurado. 

el problema muy probablemente sea que lo instalaste con sudo y lo ejecutas como usuario, o que no asignaste los correctos permisos a <alguien> para el juego. Ese alguien puede ser firewall, owner de alguna carpeta, no se.

Muchos juegos que probe yo el problema que tenian era que me los queria guardar bajo /usr (ojo, esto esta bien, solo que yo no queria que los guarde ahi, los programas en linux se guardan ahi)
y para escribir en esa carpeta necesitas permisos de root (dependiendo en que subcarpeta escribas).

Yo justo ese no lo instale, pero tengo el instalador, la proxima semana lo instalo, tengo parciales en la facu y se me complica. salu2!

---

### Post by lucasgz on 2009-10-03
bueno tal vez este haciendo algo mal pero yo no lo pude instalar sin ser superusuario. Por eso tengo que correrlo con sudo, porque sino cuando descarga los mapas no tiene los permisos para escribir la carpeta .etwolf

de todas maneras es hasta que baje todos los mapas que hay, despues ya lo voy a poder jugar sin sudo

---

### Post by pablo.s on 2009-10-03
> **lucasgz said:**
> bueno tal vez este haciendo algo mal pero yo no lo pude instalar sin ser superusuario.

Cuando bajás un .bin tenés que
darle el permiso de ejecución para
tu usuario con chmod (tanto -x como
755 valen)

---

### Post by lucasgz on 2009-10-04
volvi a bajar el instalador de la guia-ubuntu.org y me lo instalo bien ahora, puede ser que lo hallan cambiado en este tiempo? porque la instalacion era totalmente distinta
bueno ya esta resuelto gracias a todos :D

---

### Post by guillermolisi on 2009-10-04
> **lucasgz said:**
> volvi a bajar el instalador de la guia-ubuntu.org y me lo instalo bien ahora, puede ser que lo hallan cambiado en este tiempo? porque la instalacion era totalmente distinta
bueno ya esta resuelto gracias a todos :D
Todos los tutoriales que se publican pueden ser objeto de actualizaciones, mejoras, etc.

Es bueno ver en que fecha fue la ultima modificacion, sus recomendaciones previas a su aplicacion, etc.

Tema resuelto entonces :)

---

