---
title: "Problema serio con compiz (ubuntu 9.10)"
date: 2009-11-07
forum: Software
---

### Post by felipe_karmic on 2009-11-07
Hola, no quiero dar muchos preámbulos a si que les cuento de inmediato mi problema,
hoy probando los efectos de compiz se me quedo colgado el pc, todo iba de maravilla hasta que active el efecto de reflection en las ventanas, entonces se colgó y no reacciono mas, reinicie mi notebook y a penas comienza la sesion se queda colgado, bueno intente iniciar en modo de recuperación (segunda opción del grub) entonces puedo entrar a mi usuario por linea de comandos, una posible solución que veo a mi problema es editar la configuración por linea de comandos con nano, pero el problema es que no se que debo editar.

Desde ya muchas gracias por su ayuda!!!

Pd: ya probé con metacity --replace y nada por eso yo creo que la solución va por editar la configuración manualmente

SOLUCIONADO: para reiniciar la configuración borre la carpeta compiz de home/*****/.gconf/apps
donde ***** es el nombre de usuario [sudo rm -r compiz], reinicie y listo, la configuracion volvio a normal. espero que esta información le sirva a alguien en el futuro.

---

### Post by Carlos C on 2009-11-08
Felipe, gracias por aportar con la solución a tu problema, siempre es bienvenido un aporte como este.

Mi única observación es que recuerdes publicar en el subforo correspondiente.

Movido a "Software".

Saludos.

---

### Post by adirea on 2009-11-09
Gracias me viene muy bien a mí tambien, ahora nos queda ver porque se queda colgado cuando se activa compiz.
Gracias,

---

### Post by themasterdark on 2009-11-10
me paso eso mismo hace unas semanas, se cuelga el sistema al activar reflection en ventanas ...

---

