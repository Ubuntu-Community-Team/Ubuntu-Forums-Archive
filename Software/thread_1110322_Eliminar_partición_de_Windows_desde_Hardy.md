---
title: "Eliminar partición de Windows desde Hardy"
date: 2009-03-29
forum: Software
---

### Post by guidito73 on 2009-03-29
Bueno gente, estuve pensando ultimamente y me voy a librar de windows.

Actualmente uso Hardy Heron, me gustaría saber cuáles son los pasos a seguir. Tengo entendido que lo mejor es hacer un formateo general y empezar de cero nuevamente. Mi pregunta es ¿puedo mantener la partición del Home para hacer ahí el backup de todos mis datos? ¿Cómo se hace eso?

Gracias

---

### Post by Air23 on 2009-03-29
Podes hacerlo sin necesidad de formatear todo el disco.

Ante todo hace un backup de todos tus datos en dvd's o en otro disco.

Luego tenes que bootear desde el live cd de ubuntu y abir GParted (Sistema > Administracion > Editor de particiones). En estos links tenes informacion general sobre el uso de GParted:

[http://tuxpepino.wordpress.com/2007/06/13/gparted-gestiona-tus-particiones-graficamente/](http://tuxpepino.wordpress.com/2007/06/13/gparted-gestiona-tus-particiones-graficamente/)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

El primer paso es seleccionar la particion de windows (NTFS) y haces click derecho con el mouse y luego "borrar"

Luego tenes que redimensionar la particion /home (suponiendo que queres hacerlo). Tanto en [http://tuxpepino.wordpress.com/2007/06/13/gparted-gestiona-tus-particiones-graficamente/](http://tuxpepino.wordpress.com/2007/06/13/gparted-gestiona-tus-particiones-graficamente/) como en [http://gparted.sourceforge.net/larry/resize/resizing-es.htm](http://gparted.sourceforge.net/larry/resize/resizing-es.htm) tenes informacion (con capturas del programa) que te muestran como hacerlo.

Algo que puede llegar a pasar es que el espacio libre resultante de borrar la particion NTFS no este al lado de la particion /home y en ese caso tendrias que mover esta particion hasta que quede al lado del espacio libre

Un par de cosas mas. Tene en cuenta que los pasos de redimensionar y mover una particion pueden tomar mucho tiempo y acordate de hacer un backup.

---

### Post by guidito73 on 2009-03-29
Muchas gracias Air por la rápida y completa respuesta. Tengo un inconveniente, la compu que estoy usando tiene 256 MB de RAM, por lo que no puedo usar el Live CD. Se puede hacer desde Ubuntu directamente con el Gparted?

EDIT: Una cosa más: ¿qué va a pasar con el GRUB? Leí por ahí que pueden presentarse problemas después de haber eliminado la partición NTFS...

---

### Post by Mauro22 on 2009-03-29
Podes hacer siempre y cuando el Windows este instalado en otro disco, sino no podes trabajar con el Gparted, ya que necesitas trabajar sobre discos demontados...


Lo que podes hacer es bajarte el Gparted Live, que es solo eso, booteable desde un cd. (con 256 de ram, sobra y alcanza), de esa forma si podes.

---

### Post by guidito73 on 2009-03-29
Ah, esa del Gparted Live es buena... Igual, estuve viendo y si desmonto la partición NTFS puedo borrarla, no hay problema, total no la uso actualmente, ya migré todos los datos al /home.

Y en cuanto al GRUB? Qué pasa?

---

### Post by Mauro22 on 2009-03-29
Si no instalas mas nada, deberia quedar como esta, y solo te restaria editarlo para eliminar las entradas de windows.

En el caso que falle (porque todo puede fallar :D )... con el livecd de ubuntu pero en modo consola, lo tendrias que estar arreglando.


A ver quien mas opina!!

Suerte!

---

### Post by guidito73 on 2009-03-29
Claro, sería cuestión de eliminar la opción de "Other SO" (o algo así jaja) y la de Windows y listo, quedarían las 3 opciones de arranque de Ubuntu.

Bueno, voy a informarme un poco más y les aviso cómo salió la cosa.

Sigan posteando que realmente son una gran ayuda.

---

### Post by Air23 on 2009-03-29
> **guidito73 said:**
> Ah, esa del Gparted Live es buena... Igual, estuve viendo y si desmonto la partición NTFS puedo borrarla, no hay problema, total no la uso actualmente, ya migré todos los datos al /home.

Y en cuanto al GRUB? Qué pasa?
Es como decis vos, el primer paso que puse (eliminar la particion) lo podes hacer desde ubuntu una vez desmontada. El tema es que si solo haces eso estarias desperdiciando ese espacio en el disco.

Proba como te dijeron arriba con el Gparted Live ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

Una alternativa que se me ocurre (que alguien diga si me equivoco) es que en vez de eliminar la particion de windows la formatees como EXT3, luego la montas en tu home (por ejemplo /home/usuario/datos) y la usas para almacenar datos o lo que quieras.

---

### Post by guidito73 on 2009-03-29
Bueno, me apresuré a hacerlo, eliminé la partición y ahora me quedó así como en el screenshot.

De tal manera que no puedo redistribuirlo entre el root y el home.

¿Qué hago?

---

### Post by Air23 on 2009-03-29
> **guidito73 said:**
> Bueno, me apresuré a hacerlo, eliminé la partición y ahora me quedó así como en el screenshot.

De tal manera que no puedo redistribuirlo entre el root y el home.

¿Qué hago?
No se puede agrandar ninguna de las particiones desde ubuntu porque las estas usando

Si queres agrandar la particion tenes que hacerlo desde el GParted live (o si pudieras desde el live cd de ubuntu)

---

### Post by guidito73 on 2009-03-29
No, desde el Gparted Live tampoco pude hacerlo... =S

Es como que no quedara dentro del "sda" (ni idea que es :P) entonces no me deja asignar el espacio vacío a las otras particiones...

---

### Post by staar on 2009-03-29
me parece que primero vas a tener que mover las dos particiones que te quedaron al principio del disco, y recien ahi les vas apoder asignar el espacio libre, OJO, que es un proceso que lleva bastante tiempo, algunas horas dependiendo de la velocidad del disco y de la maquina...

saludos

---

### Post by Air23 on 2009-03-29
> **staar said:**
> me parece que primero vas a tener que mover las dos particiones que te quedaron al principio del disco, y recien ahi les vas apoder asignar el espacio libre, OJO, que es un proceso que lleva bastante tiempo, algunas horas dependiendo de la velocidad del disco y de la maquina...

saludos
Exactamente eso estaba por decir :)

Move las particiones de manera que queden asi: sda5 (root) - sda7 (swap) - sda6 (home) quedando el espacio libre a la derecha de la particion que queres agrandar. Luego deberias poder agrandar la particion de 17 Gb.

---

### Post by guidito73 on 2009-03-29
Listo listo gente!

No me había percatado de mover las particiones! Ya está todo listo, en 30 minutos hice todo y quedó todo el espacio distribuido. Hermoso.

Les agradezco a todos por la onda.

---

### Post by Air23 on 2009-03-29
> **guidito73 said:**
> Listo listo gente!

No me había percatado de mover las particiones! Ya está todo listo, en 30 minutos hice todo y quedó todo el espacio distribuido. Hermoso.

Les agradezco a todos por la onda.
De nada y felicitaciones por eliminar windows

---

