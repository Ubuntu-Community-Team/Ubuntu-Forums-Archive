---
title: "pide clave luego de suspender"
date: 2011-01-26
forum: Software
---

### Post by joseluis on 2011-01-26
amigos,
instalé ubuntu 10.04.2 en una portátil lenovo g550.
la cosa es que luego de suspender siempre me pide contraseña.
a pesar de que deshabilité esa opción desde el config-edit/apps/etc etc....destildndo esa opción.
no se qué hacer para que no me pida mas la contraseña. Espero puedan ayudarme, 
gracias

---

### Post by guillermolisi on 2011-01-27
Sabes si esa contraseña se pide desde Gnome o desde el BIOS de la maquina ?

---

### Post by joseluis on 2011-01-27
si, la pide desde Gnome.
Uso ubuntu 10.04.
el tema extraño está en que si bajo la tapa de la notebook, que se suspende, al abrir la tapa sin problemas se activa toda la compu y no pide contraseña.
En cambio, si voy a icono de apagar/suspender, se suspende , pero si quiero volver a activar, ahi me pide la contraseña.

---

### Post by juancarlospaco on 2011-01-27
Se me hace que tenes auto-login*(?)*, y al volver de suspension alguna interfaz de comunicaciones se vuelve a activar, pidiendo clave.

---

### Post by joseluis on 2011-01-27
si auto login es tener seteado que "ingrese directamente, sin pedir contraseña", si.

---

### Post by joseluis on 2011-01-28
> **juancarlospaco said:**
> Se me hace que tenes auto-login*(?)*, y al volver de suspension alguna interfaz de comunicaciones se vuelve a activar, pidiendo clave.

y entonces que hacer?

---

### Post by joseluis on 2011-05-06
bueno..despues de mucho tiempo de lidiar con esto, el asunto sigue. Puse 11.04 y sigue haciendo lo mismo. Por favor,es muy incómodo y no encuentro en internet la solución.

---

### Post by guillermolisi on 2011-05-06
Desde la optica de la seguridad, me parece perfecto que cuando se reanima la PC luego de haberla suspendido solicite clave sencillamente porque la maquina pudo haber caido en manos ajenas estando suspendida.

Mi consejo es no modificar esa funcionalidad, aunque uno tenga que molestarse ingresando la password cada vez que se reanima luego de una suspension.

---

### Post by joseluis on 2011-05-06
ok..de acuerdo, pero si no lo quisiera? hay modo de que no aparezca?

---

### Post by guillermolisi on 2011-05-06
Usas salvapantalla ? Fijate si esta marcada la opcion de solicitar clave cuando se vuelve a la sesion (block screen en Ingles).

---

### Post by joseluis on 2011-05-06
si, esta desmarcada, PERO ENCONTRE LA SOLUCION!!!!!!!!!!!

aca esta, [http://www.taringa.net/posts/linux/7544562/evitar-que-Ubuntu-pida-contrasena-tras-suspender.html](http://www.taringa.net/posts/linux/7544562/evitar-que-Ubuntu-pida-contrasena-tras-suspender.html)

y funciona tal como quería

---

