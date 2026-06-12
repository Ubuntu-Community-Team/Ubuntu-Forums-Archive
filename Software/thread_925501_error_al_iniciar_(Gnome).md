---
title: "error al iniciar (Gnome)"
date: 2008-09-20
forum: Software
---

### Post by granjero on 2008-09-20
queria saber por que puede haber salido este error?

gracias!



"Ha ocurrido un un error al iniciar el demonio del Administrador de Preferencias de GNOME.

Algunas cosas como las configuraciones de temas, sonidos o fondo de pantalla puede que no funcionen correctamente.

El último mensaje de error fue:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME seguirá intentando reiniciar el Demonio de Preferencias la próxima vez que inicie una sesión."

---

### Post by phxnd on 2008-09-22
a mi tambien me pasa aveces, no me acuerdo por que xD
que placa de video tenes?¿

---

### Post by donmatas on 2009-07-30
A mi me acaba de pasar por primera vez desde que instalé (1 semana). Pero además he tenido problemas cuando incio la computadora, pues no siempre carga el panel a la resolución adecuada. Además, aveces al apagarlo, queda todo en negro pero prendido.

Mi laptop es una inspiron 1545 (hardy) y mi tarjeta de video es 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

EL mensaje completo es:
Ha ocurrido un un error al iniciar el demonio del Administrador de Preferencias de GNOME.

Algunas cosas como las configuraciones de temas, sonidos o fondo de pantalla puede que no funcionen correctamente.

El último mensaje de error fue:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME seguirá intentando reiniciar el Demonio de Preferencias la próxima vez que inicie una sesión.

---

### Post by phxnd on 2009-07-30
wow un problema j****o que ya tienen sus años casi
alto revive

---

### Post by aledruetta on 2009-07-31
Pegando el texto del error en el buscador Google, en una de las listas de correo que aparecen, recomiendan ejecutar en consola este comando:
```
gnome-settings-daemon &
```
Podrías probarlo a ver qué pasa, si te animás.

Saludos,
Alejandro.

---

