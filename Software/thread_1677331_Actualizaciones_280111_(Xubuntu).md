---
title: "Actualizaciones 28/01/11 (Xubuntu)"
date: 2011-01-28
forum: Software
---

### Post by Liv~ on 2011-01-28
Hola a todos.
El gestor de actualizaciones me dice que hay una serie de actualizaciones recomendadas que por lo que veo tienen que ver con el kernel. 
No sé exactamente para qué son ni qué hacen ni nada, pero como están relacionadas al kernel no quiero mandarme ninguna, por eso recurro a ustedes.

Les adjunto un screenshot de las actualizaciones en cuestión.
Quedan 2 que no salen en el screen que dicen:

"GNOME application that manages apt updates"
(update-manager)
"manage release upgrades"
(update-manager-core)


Tengo Xubuntu Maverick. 
Ya sé que tal vez sea una tontería pero antes que actuar sin tener conocimiento, prefiero preguntar.
Es seguro que instale estas actualizaciones o mejor dejo todo como está?


Desde ya gracias.

---

### Post by marcelo_bur on 2011-01-28
Hola. No tendría porque haber ningun problema al instalar las actualizaciones automáticas, ya sean del kernel u otras librerias, asi como también suelen cada tanto aparecer actualizaciones de algunos programas. Mi escasa experiencia me dice que con lo que hay que tener cuidado en con actualizaciones manuales de algunos programas, asi como habilitar repositorios que no son los predeterminados del sistema. Pero supongo que ya alguien con mayores conocimientos te aclarará estos puntos. Por el momento no veo inconveniente en que instales las actualizaciones.
Saludos

---

### Post by z37a on 2011-01-29
Actualiza tranquilo, que si no te funciona, como es un nuevo kernel, en el grub apenas inicie vas a poder elegir el kernel que usabas antes y listo!

---

### Post by Liv~ on 2011-01-30
Pero en caso que tenga que volver al viejo kernel, cómo hago para elegirlo al inicio? Digo, porque cuando prendo la pc lo único que veo es una pantalla con el logo de Xubuntu mientras carga y después ya viene la pantalla de login... 
O en caso de haber algún problema me aparece para elegir el kernel automáticamente?

Gracias a ambos por sus respuestas!

PD: z37a, soy mujer :P

---

### Post by atari130xe on 2011-01-30
> **Liv~ said:**
> Pero en caso que tenga que volver al viejo kernel, cómo hago para elegirlo al inicio? Digo, porque cuando prendo la pc lo único que veo es una pantalla con el logo de Xubuntu mientras carga y después ya viene la pantalla de login... 
O en caso de haber algún problema me aparece para elegir el kernel automáticamente?

Gracias a ambos por sus respuestas!

PD: z37a, soy mujer :P

Por regla general cuando en Ubuntu se actualizan kernels tambièn se actualizan las entras en el menù de GRUB por lo tanto con solo bajar con el cursor al ùltimo kernel que tenìas antes de actualizar es suficiente, sin miedo, que funciona bièn.

---

### Post by z37a on 2011-01-31
> **atari130xe said:**
> Por regla general cuando en Ubuntu se actualizan kernels tambièn se actualizan las entras en el menù de GRUB por lo tanto con solo bajar con el cursor al ùltimo kernel que tenìas antes de actualizar es suficiente, sin miedo, que funciona bièn.

Atari, a mi me paso que el grub si tenes solo Ubuntu y nada mas no te muestra otras opciones, queda oculto, para solucionarlo edite al archivo del grub, la verdad fue complicado (para un usuario amateur), igualmente Liv~ no deberías tener problemas!


Agrego:

Para permitir ver el menu del GRUB en caso que durante el boot no se muestre hay que editar al archivo /etc/default/grub:

sudo nano /etc/default/grub

Y alli comentar las lineas:

#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true

por ultimo: sudo grub-install (igual aca tengo mi duda con este ultimo comando, igualmente si podes hace la modificación del archivo antes de actualizar, luego al actualizar el grub se reinstalara y aplicara esa opción).

---

### Post by Liv~ on 2011-01-31
Claro, a eso me refería cuando pregunté cómo hacía para elegir el kernel al inicio porque como tengo Xubuntu sólo instalado, me aparece oculto, por eso les dije que al inicio sólo veía el logo y nada más.

Bueno, de todas maneras, acabo de actualizar y aparentemente todo bien!

Gracias nuevamente por la ayuda y buena onda a los 3!

---

### Post by asterix77 on 2011-02-01
Cuando haces una instalación limpia de ubuntu, es decir sin ningún otro sitema operativo, por defecto no aparece el grub, por lo que puedes tener varios kernel, pero siempre el sistema ingresará al más reciente. Solo editando el  grub harás que aparezca al principio; creo que también presionando Mayúsculas durante el inicio del Sistema, también lo puedes ver.

Lo bueno de tener el grub, es que si por cualquier motivo una actualización del kernel no te arranca, o te dá problemas, puedes escoger otro.


Saludos

---

### Post by z37a on 2011-02-01
> **asterix77 said:**
> Cuando haces una instalación limpia de ubuntu, es decir sin ningún otro sitema operativo, por defecto no aparece el grub, por lo que puedes tener varios kernel, pero siempre el sistema ingresará al más reciente. Solo editando el  grub harás que aparezca al principio; creo que también presionando Mayúsculas durante el inicio del Sistema, también lo puedes ver.

Lo bueno de tener el grub, es que si por cualquier motivo una actualización del kernel no te arranca, o te dá problemas, puedes escoger otro.


Saludos

Muy buen dato eso del shift, lastima que mi grub lo modifique a propósito y no voy a poder probarlo, pero me parece muy útil eso, así se evitaría modificarle las opciones pro defecto.

---

