---
title: "Quitar mostrar tareas en AW"
date: 2009-10-16
forum: Software
---

### Post by matias_tati on 2009-10-16
Hola tengo instalado avant windows navigator y queria saber si hay una forma de que este no me muestre los programas ni las ventanas abiertas, ya que tengo esta funcion en la bara de arriba.
Gracias....

---

### Post by FB91 on 2009-10-16
Yo también quise hacer lo mismo pero nunca encontré la manera...

Así que si alguien sabe como hacerlo mil gracias

---

### Post by santiagoward2000 on 2009-10-16
Hola!
Según este blueprint: [https://blueprints.launchpad.net/awn/+spec/allow-launcher-only]("https://blueprints.launchpad.net/awn/+spec/allow-launcher-only") por ahora no se puede porque los lanzadores y las tareas son parte del mismo módulo, pero están pensando separarlos para la versión 0.4.
Mientras esperan, podrían probar con otro dock. Por ejemplo, yo tengo Cairo-Dock-2, y se puede desactivar (así lo tengo yo).
Saludos!

---

### Post by matias_tati on 2009-10-22
> **santiagoward2000 said:**
> Hola!
Según este blueprint: [https://blueprints.launchpad.net/awn/+spec/allow-launcher-only]("https://blueprints.launchpad.net/awn/+spec/allow-launcher-only") por ahora no se puede porque los lanzadores y las tareas son parte del mismo módulo, pero están pensando separarlos para la versión 0.4.
Mientras esperan, podrían probar con otro dock. Por ejemplo, yo tengo Cairo-Dock-2, y se puede desactivar (así lo tengo yo).
Saludos!

Y una pregunta en el cairo dock se puede poner como opcion que los iconos cambien con el pack de iconos instalados?

---

### Post by santiagoward2000 on 2009-10-23
> **matias_tati said:**
> Y una pregunta en el cairo dock se puede poner como opcion que los iconos cambien con el pack de iconos instalados?

Sí, pero depende, jeje. Si usás uno de los temas armados, no, porque apuntan a una ubicación fija. Tenés que editar cada uno por separado para ponerle solo el nombre del ícono (por ejemplo ponés **pidgin** en vez de **~/.icons/Nombre_del_Tema/pidgin.png**).
Si arrancás con un tema ya armado es un parto cambiarlos uno por uno, pero si lo armás vos de cero es más simple (sólo arrastrás los íconos desde el menú, si lo siguen ahí lo van a seguir en el dock también).
Saludos!

---

### Post by leosr on 2009-10-28
Hola.
Entrás en el "Sistema - Preferencias - Awn Manager - Applets" y desactivás Launcher/Taskmanager y listo.

Salu2.

---

### Post by matias_tati on 2009-10-28
> **leosr said:**
> Hola.
Entrás en el "Sistema - Preferencias - Awn Manager - Applets" y desactivás Launcher/Taskmanager y listo.

Salu2.

Si hago eso se me van tmbn todos los lanzadores.
Gracias.

---

### Post by Mauro22 on 2009-10-28
[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1721&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1721&page=1&isLive=true)

[http://moon-shiny.blogspot.com/2008/02/simple-launcher.html](http://moon-shiny.blogspot.com/2008/02/simple-launcher.html)

??

---

### Post by santiagoward2000 on 2009-10-28
> **Mauro22 said:**
> [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1721&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1721&page=1&isLive=true)

[http://moon-shiny.blogspot.com/2008/02/simple-launcher.html](http://moon-shiny.blogspot.com/2008/02/simple-launcher.html)

??

Mmm, ese blog tira un link al [PPA de AWN]("https://launchpad.net/~awn-testing/+archive/ppa"), donde ya subieron la versión 0.3.9.1 (calculo que debe ser una versión preliminar de la 0.4) que aparentemente ya trae ese módulos separados. Buena Mauro22!

---

