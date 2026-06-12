---
title: "[SOLVED] Apagar el equipo hardy 32 bits"
date: 2008-09-20
forum: Software
---

### Post by ramiro_md on 2008-09-20
Hola, muy buenos días, resulta que ayer por la tarde vole hardy de 64 bits y puse la versión de 32. La cuestión es que todo iba bárbaro hasta que ayer por la noche actualice el sistema, debido a que después de eso no pude volver a apagar el equipo normalmente.
CUando utilizo la opción "sistema > salir" el sistema se cuelga =S y si utilizo desde consola "shutdown now" cierra la sesión y se sale al "recovery menu". No tengo mucha idea de como solucionar esto, tengo miedo de que tenga que volver a instalar hardy ¬¬. Espero que me puedan ayudar, un saludo.

---

### Post by ramiro_md on 2008-09-20
Se solucionó solo :)

---

### Post by Kabezon on 2008-09-23
A mí me pasa lo mismo, creo... Onda que el coso para apagar no carga más, y en esos 40 a 60 segundos que se demora en salir no me deja hacer nada :S Nada se cuelga, simplemente se demora una vida en cargar el... coso este.

---

### Post by ramiro_md on 2008-09-23
Si tal cual, hay veces que se tarda y otras que me lo hace de una asique ni me preocupo xq a la larga temina apareciendo. Asique le chante solved y lesto. UN saludo

---

### Post by Mister X on 2008-09-23
el responsable de que tarde una eternidad en cargar la ventana con las opciones de salida es que no se esté ejecutando el proceso gnome-power-manager, fijense si lo deshabilitaron en el inicio de Gnome (sesiones-> gestion de energia)

para ver si está corriendo:

```
ps -A|grep gnome-power-ma
```

---

### Post by ramiro_md on 2008-09-24
Gracias man !!, ese mismo era el problema. Ahora esta "solved" en serio el problema :)

---

### Post by Kabezon on 2008-09-24
Mil gracias :D

---

### Post by valucha on 2008-09-25
[COLOR="DarkOrchid"]Desactivaste el powernowd o power-manager de los servicios de inicio o algo así?... es algo que muchos manuales de optimización te dicen que desactives proque es para laptocs y que no te sirve... Pero genera eso... que el cartel tarde millooones de años en aparecer. Fijate si es eso.

Saludos.[/COLOR]

---

### Post by ramiro_md on 2008-09-25
Si valucha, gracias por atender el post, igualmente ya lo solcuioné. Pero fue lo primero que hice cuando me surgió el problema y acudí a un thread tuyo de hace tiempo atrás. Un saludo.

---

