---
title: "Ayuda con VirtualBox"
date: 2008-09-06
forum: Software
---

### Post by Marcos Repezza on 2008-09-06
quiero ejecutar el windows xp en mi ubuntu pero no logro hacerlo lei todos los tutoriales que hay pero explican como hacerlo e instalar luego el windows de haber instalado el virtualbox el problema es que yo ya tengo instalado el Xp en el disco sda1 es decir tengo instalado el ubuntu en una particion y el xp en otra particion cuando prendo la pc arranca con linux si es que no le doy a la opcion de iniciar con windows. mi pregunta es: ¿Como puedo configurar el VirtualBox para que me bootee el windows que tengo instalado para asi poder ejecutarlo dentro de mi Ubuntu?

Desde ya Muchas Gracias

---

### Post by guillermolisi on 2008-09-06
> **Marcos Repezza said:**
> quiero ejecutar el windows xp en mi ubuntu pero no logro hacerlo lei todos los tutoriales que hay pero explican como hacerlo e instalar luego el windows de haber instalado el virtualbox el problema es que yo ya tengo instalado el Xp en el disco sda1 es decir tengo instalado el ubuntu en una particion y el xp en otra particion cuando prendo la pc arranca con linux si es que no le doy a la opcion de iniciar con windows. mi pregunta es: ¿Como puedo configurar el VirtualBox para que me bootee el windows que tengo instalado para asi poder ejecutarlo dentro de mi Ubuntu?

Desde ya Muchas Gracias
Marcos

VirtualBox, al igual que otros productos similares, te permite virtualizar una PC.
Esto es: Corres/haces funcionar una maquina dentro de otra.
No sirve para dual boot.

Si queres correr una maquina con XP en la PC que usas con Ubuntu (la PC fisica), inicias VBox y le instalas el XP como si fuera una PC comun y corriente luego de haber definido que caracteristicas tendra esa PC virtual (tamaño de RAM, tamaño de discos rigidos, etc.).

---

### Post by Marcos Repezza on 2008-09-06
Aja osea que no puedo hacer lo que digo con virtualbox... lo puedo hacer con otra aplicacion parecida a vbox? o estamos en la misma, que me recomendas?

---

### Post by guillermolisi on 2008-09-06
> **Marcos Repezza said:**
> Aja osea que no puedo hacer lo que digo con virtualbox... lo puedo hacer con otra aplicacion parecida a vbox? o estamos en la misma, que me recomendas?
No conozco si hay alguna aplicacion que permita correr en forma concurrente XP instalado en una particion en una PC con Ubuntu, salvo la virtualizacion (pero que usa su propia estructura para alojar el SO huesped).

En general, cuando existe esa configuracion de sistemas operativos instalados en una misma PC (en distintas particiones del HD) se utiliza dual boot, pero no es concurrente sino alternativo excluyente (o uno o el otro).

---

### Post by ariel on 2008-09-06
> **Marcos Repezza said:**
> Aja osea que no puedo hacer lo que digo con virtualbox... lo puedo hacer con otra aplicacion parecida a vbox? o estamos en la misma, que me recomendas?

En teoria vmware puede hacerlo, pero es muy complejo. Antes de virtualizar, hay que lograr instalar los drivers de vmware en el futuro guest XP, y dependiendo de tu instalacion cambiar el kernel de windows (windows trae varios, pero solo se instala uno durante el proceso de instalacion). No conozco a nadie que haya logrado hacerlo funcionar.

Te recomiendo VirtuaBox (recien salio la version 2.0), y crear una maquina virtual nueva con un disco virtual (archivo) de 8GB. Para instalar office y otras aplicaciones de oficina, sobra. Y bootea en 10 segundos.

---

### Post by guillermolisi on 2008-09-06
> **ariel said:**
> En teoria vmware puede hacerlo, pero es muy complejo. Antes de virtualizar, hay que lograr instalar los drivers de vmware en el futuro guest XP, y dependiendo de tu instalacion cambiar el kernel de windows (windows trae varios, pero solo se instala uno durante el proceso de instalacion). No conozco a nadie que haya logrado hacerlo funcionar.

Te recomiendo VirtuaBox (recien salio la version 2.0), y crear una maquina virtual nueva con un disco virtual (archivo) de 8GB. Para instalar office y otras aplicaciones de oficina, sobra. Y bootea en 10 segundos.

Coincido, para usar en forma concurrente (aunque en realidad sean dos entornos bien separados), virtualizar el XP es la opcion recomendada.

Es mas, salvo por las caracteristicas de Win respecto de estabilidad, si se te corta la luz en mitad de algo la VM ni se inmuta. La volves a iniciar y listo. 

Tambien podes hacer snapshots de la VM antes de instalar algo en el XP para probar. Si no resulta como pensabas, volves a la imagen anterior y listo, no paso nada.

Ademas, VBox tiene una funcion que te permite integrar el escritorio virtualizado al real que me parecio muy buena. Lo hace mas transparente aun.
Si no te gusta como es, con un par de click volves a la vista normal (en una ventana o pantalla completa).

Una vez que tengas replicado tu XP en la VM tranquilamente podes borrar la particion que tiene XP e integrar ese espacio a Ubuntu.

Un detalle: Ojo con los juegos que necesitan de aceleracion 3D en Windows.

---

### Post by Marcos Repezza on 2008-09-06
ok chicos muchas gracias por la ayuda voy a probar como me dijeron para ver como queda, si estoy conforme les hare saber...
Gracias Nuevamente!

---

### Post by autusgo on 2009-10-31
Sé que esto es de hace tiempo, pero quiero sacarme una duda. Estuve leyendo por ahí que se puede crear un archivo vdmk (todavía no sé como) que es como una imagen de un sistema operativo ya instalado en la PC, y así correr un Windows de otra partición, en VirtualBox. Es así o entendí cualquier cosa?

---

### Post by guillermolisi on 2009-10-31
> **autusgo said:**
> Sé que esto es de hace tiempo, pero quiero sacarme una duda. Estuve leyendo por ahí que se puede crear un archivo vdmk (todavía no sé como) que es como una imagen de un sistema operativo ya instalado en la PC, y así correr un Windows de otra partición, en VirtualBox. Es así o entendí cualquier cosa?
El tema de virtualizar maquinas es independiente de que particion se use.

Podes tener una VM que utilice espacio de disco de una o mas de una particion (en realidad dependera de como se dispongan los puntos de montaje y los Shared Folders para el caso de VBox).

Luego, la imagen de una maquina virtual (ese archivo vdmk y no recuerdo si hace falta alguno otro) se puede llevar y utilizar en otra PC como si se hubiera generado ahi mismo. Esta caracteristica es una de las que posibilita esquemas de alta disponibilidad ciertamente economicos (se cae un host y hago correr una copia de la VM en otro que funcione).

---

### Post by z37a on 2009-11-01
> **guillermolisi said:**
> El tema de virtualizar maquinas es independiente de que particion se use.

Podes tener una VM que utilice espacio de disco de una o mas de una particion (en realidad dependera de como se dispongan los puntos de montaje y los Shared Folders para el caso de VBox).

Luego, la imagen de una maquina virtual (ese archivo vdmk y no recuerdo si hace falta alguno otro) se puede llevar y utilizar en otra PC como si se hubiera generado ahi mismo. Esta caracteristica es una de las que posibilita esquemas de alta disponibilidad ciertamente economicos (se cae un host y hago correr una copia de la VM en otro que funcione).

Como poder se podria utilizar una partición de un dual boot para iniciar en una maquina Virtual, como comentaron VMware lo permite, también se podría hacer con Xen, y supongo que lo mismo con KVM. Pero esto no siempre va a funcionar, ya que si usas un Windows y a este le cambias el hardware vas a tener un bonito bluescreen(BSOD).

Como dice guillermo también al generar un disco virtual podes moverlo de una pc a otra y utilizarlo, peor esto solo funciona si la otra PC es de la misma arquitectura, dependiendo de la herramienta de virtualizacion si creas una maquina virtual en un AMD no te va a andar en un Intel, como ejemplo, pero esto también va en el Windows, ya que al ser distinta arquitectura necesita drivers que no tiene y BSOD.

En todo caso VirtualBox no permite utilizar una partición como disco virtual, pro ende no te va a servir, VMware tal vez te sirva, y también es gratuito. Xen y KVM me parece que también te van a servir, peor no se cmo0 se va a comportar un windows ahi.

---

### Post by guillermolisi on 2009-11-01
> **z37a said:**
> 
Como dice guillermo también al generar un disco virtual podes moverlo de una pc a otra y utilizarlo, peor esto solo funciona si la otra PC es de la misma arquitectura, dependiendo de la herramienta de virtualizacion si creas una maquina virtual en un AMD no te va a andar en un Intel, como ejemplo, pero esto también va en el Windows, ya que al ser distinta arquitectura necesita drivers que no tiene y BSOD.

Sobre ese tema de las arquitecturas tengo mis dudas ya que una de las caracteristicas mas interesante de la virtualizacion es la abstraccion del hardware del host (pero esto ya es casi un OT respecto de este thread).

---

