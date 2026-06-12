---
title: "Problemas de arranque"
date: 2009-12-09
forum: Software
---

### Post by arturojgt on 2009-12-09
Hola a todos. tengo un pequeño problema el cual es el sig:
tengo una eeepc 1000ha, le saque el xp que trae y puse karmic. tengo una particion ntfs de 180 para guardar cosas y me que da 80 g libres el cual asigne 20 al karmic. pero por motivos de trabajo hay progs que corren solo en win y cuando quise instalarlo de nuevo (7, xp o vista) lo instalo sin dramas pero al momento de reiniciar, en el arranque me sale una pantalla negra con el cursor parpadeando arriba y ahi se queda...no pude solucionar con ninguna de la 3 distro de windows..aun formatenado o borrando la particion. Pero el karmic o jaunty se instalan sin drama..me reconocen la instalacion de win en el grub pero cuando la selecciono de nuevo la pant negra...alguien que me ayude porf :-k. pd: intente partition, acronis, etc. y no pasa nada.

---

### Post by guillermolisi on 2009-12-09
Cada vez que instales Win, en las versiones que sean, se rompe el administrador de inicio (Grub para Linux) y tenes que recuperarlo para que quede reconstruido.

El proceso correcto es instalar primero Win y despues Ubuntu, asi no tendras los problemas que experimentas.

---

### Post by arturojgt on 2009-12-09
Si. es asi como me lo decis..pero el drama es que el problema es que al querer arrancar windows habiendo instalando linux despues ( o sacandolo completamente linux) el arranque queda en la pantalla negra con el cursor (ningun mensaje de error). Linux se instala perfectamente y no me da ese error. me fije en los otros post y no consigo arreglarlo

---

### Post by guillermolisi on 2009-12-09
Dale una leida a [este thread]("http://ubuntuforums.org/showthread.php?t=1348022&highlight=grub") que posiblemente la cosa venga por el lado del Grub2 (bah, 1.97)

---

