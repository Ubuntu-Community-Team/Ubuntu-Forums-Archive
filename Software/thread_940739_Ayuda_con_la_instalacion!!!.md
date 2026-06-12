---
title: "Ayuda con la instalacion!!!"
date: 2008-10-07
forum: Software
---

### Post by Mikha90 on 2008-10-07
Buenos dias!
Les cuento que estoy intentando instalar Linux en mi pc, poseo los cd de Ubuntu 8.04 y Kubuntu 8.04.

El problema es que no se que pasa, pero la instalacion no arranca con ninguno de los 2, osea, bootea el cd, entra en la pantalla, le doy a la opcion que instale, carga y despues queda en una pantalla negra que da una presentacion de algo arriba, pero nada mas.

Sera algo de la configuracion? O del hadware tal vez?

Mi pc es una AMD Athlon 64 3000+, tiene 2 discos SATA, un Hitachi de 80 Gb y un Werstern de 160 Gb que en donde deseo instalar.
Pero a su vez ese disco esta dividido en particiones de 50, 70 y 40 Gb (en la de 50 tengo Xp, la de 70 es de archivos y la restante seria para linux). La pc bootea sobre el disco de 80Gb, el cual posee otro Xp, y de ahi da la opcion de elegir que sistema operativo desea utilizar.

Espero haber puesto todo lo necesario para que se entienda, y perdon por lo que no se entienda!

Desde ya muchas gracias a todos!
Saludos!

---

### Post by ssthormess on 2008-10-07
No te carga el [K]Ubuntu en Live?.. 

PD: Disculpame pero no lo especificaste, asi que no lo se.

---

### Post by Mikha90 on 2008-10-07
No arranca en "Probar K/Ubuntu". A ambos Cd's les hice comprobacion de integridad, pero nada.
:(

---

### Post by ssthormess on 2008-10-07
¿Me podrias decir hasta que punto llegas? y ¿Que pasa cuando llegas a ese punto?

---

### Post by Mikha90 on 2008-10-07
Pongo el cd, bootea, selecciono el idioma, pongo instalar, luego carga una barrita y despues aparece un logo con una barra que se mueve por debajo como cargando, pasa a una pantalla negra en la cual dice:
"Busy box (etc, etc, etc) Built-in shell (ash)
(etc, etc, etc)
(initramfs)"
Y alli queda, no hace mas nada.

---

### Post by WanderingKnight on 2008-10-07
Ehm, aparentemente te tira a una consola de rescate (Busybox).

Fijate si apretando la tecla que se indica al principio como "Indicar parametros de arranque" o algo asi, y agregando alguno de estos dos parametros a la linea que vas a ver:

```
noapic
nolapic
```

arranca.

---

### Post by Mikha90 on 2008-10-07
Probe como me dijiste y no hubo cambios, todo sigue igual. :(

---

### Post by WanderingKnight on 2008-10-07
En lugar de agregar eso agregá

```
all_generic_ide
```

y fijate qué pasa.

---

### Post by Mikha90 on 2008-10-07
Gracias! logre instalarlo! :D
Ahora tengo una duda, puedo modificar la parte de booteo en la que me permite selecciona el sistema operativo? Quisiera poner que por defecto arranque sobre el Windows, ya que mis hermanos no usan linux.

---

### Post by pol666 on 2008-10-07
sudo apt-get install startupmanager

Ahi tenes un programita copado que deja configurar el arranque

---

### Post by pol666 on 2008-10-07
sudo apt-get install startupmanager

Ahi tenes un programita copado que deja configurar el arranque

---

### Post by victor_nesta on 2008-10-07
Che, perdón por la pregunta.
Pero, ¿para que o por que debe ingresar esos parámetros en la instalación?
Me imagino por el nombre, pero como quedo demostrado la suposición no es lo mio, jeje.
Capaz que algún día me pasa, por eso pregunto. 
Gracias

---

### Post by WanderingKnight on 2008-10-07
> 
Pero, ¿para que o por que debe ingresar esos parámetros en la instalación?

Si te digo te miento. Lo que encontré googleando fue [este](https://bugs.launchpad.net/ubuntu/+bug/217616) bug.

El noapic/nolapic generalmente tiene que ver con falta de soporte del ACPI del mother (porque muchas veces los fabricantes mandan cualquiera con eso). La verdad no sé qué hace exactamente el all_generic_ide, pero por lo que llego a leer tiene que ver con algún tipo de incompatibilidad con ciertos discos rígidos. El problema pasa porque por alguna razón extraña el Live CD no logra montar los discos correctamente... de ahí a qué hace exactamente esa línea, sabés tanto como yo al respecto.

---

### Post by ssthormess on 2008-10-12
Pues, este tema deberia marcarse como solucionado.

---

### Post by majatu on 2008-10-12
Con el administrador de arranque que te pasaron mas arriba yo le deje a mi vieja que arranque por defecto XP y de paso te deja modificar los colores, ponerle imagen de fondo y personalisar como quieras el grub

Salutes!

---

### Post by marro on 2008-10-13
hola, acabo de instalar el Ubuntu 6.06.1 lts y cuando reinicio la pc sin el cd me aparece un log in tipo el dos de windows.. no se que hacer para entrar.. es la primera vez q instalo linux.. pongo oem como usuario porque no se donde lei y no se q hacer.. ayuda por favor:confused:

---

### Post by pol666 on 2008-10-13
por que estas usando una version tan vieja.

---

