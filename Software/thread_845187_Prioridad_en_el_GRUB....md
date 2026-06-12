---
title: "Prioridad en el GRUB..."
date: 2008-06-30
forum: Software
---

### Post by grsshppr on 2008-06-30
Hola! me gustaría saber si hay alguna manera de poner al XP primero en el GRUB, para que si no se elige ninguna opción entre a Windows por defecto. Hago esta pregunta porque hace poco instalé Xubuntu 8.04 y como no soy el único que usa la pc en mi casa todos me **** cuando se meten a xubuntu sin querer...

Ah, y mi otra pregunta es ¿como configurar el modem prestige 600 series de speedy en xubuntu?

---

### Post by anka on 2008-06-30
Para la primera tienes este post:

[http://ubuntuforums.org/showthread.php?t=524134](http://ubuntuforums.org/showthread.php?t=524134)

Cambia kate por tu editor (no recuerdo cual trae xubuntu, creo que lo use una sola vez)

Para el segundo hay un par de post por ahi pero no se si es el mismo mismo que tienes tu.

Prueba poner el nombre de tu modem en el buscador del foro, saldran varios posts.

Suerte!!

---

### Post by feche_mza on 2008-07-01
***para el grub proba instalando el administrador de arranque , esta en los repositorios, es mas o menos lo mismo que te paso anka nada mas que en modo grafica y es re facil de usar, y para internet no se bien que modem es pero si en win tenias que poner el nombre de usuario y contraseña proba poniendo en terminal*** sudo pppoeconf ***o si no en el panel te aparecen 2 PCs(como en win)cuando clikeas te aparece la opcion configuracion manual, metete desbloquealo y en conexion cableada pone las propiedades y selecciona*** DHCP [B][I](desactivas el modo itinerante obvio)
y listo solo se configura, ahora ya sea que lo configures con la ip estatica(por terminal) o con[/I][/B] DHCP ***no te van a andar los 2 juntos tenes que hace uno o el otro ***

---

### Post by santiagoward2000 on 2008-07-03
Hola!
La forma más simple es instalando el **Startup-Manager**. En una consola poné:
```
sudo apt-get install startupmanager
```
Después, abrilo (creo que está en Applications/System) y elegí qué sistema queres por defecto.
Puede que tengas que volver a configurarlo si alguna vez actualizas es kernel.
Saludos!

---

### Post by excaliburs on 2008-07-18
edita el menu.lst

# sudo gedit /boot/grub/menu.lst

pones el login cuando te lo pida

una vez dentro de menu.lst cambia la entrada que dice default 0 por el numero que ocupe win dentro de la lista.....
0 es el primer booteo 1 el que le sigue y asi hasta llegar al ultimo....conta en que lugar esta win y pone el numer en lugar del 0

saludos.

---

### Post by excaliburs on 2008-07-18
perdon....eso me pasa por no haber seguido el link de anka....no dije nada..

---

