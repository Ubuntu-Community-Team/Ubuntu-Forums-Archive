---
title: "Audacity graba solo 3 segundos"
date: 2010-04-16
forum: Software
---

### Post by granjero on 2010-04-16
Buenas gente.... ando con un tema. 
Cuando pongo a grabar con audacity graba sólo los 3 primeros segundos....

además el uso de cpu se dispara al 100% en uno de los núcleos... 

```
jm@pcjm:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```

a alguien se le ocurre que puede ser?

necesito que ande... porque si no se van a reir de mi y de ubuntu.... :(:(:(:(


gracias de antemano!

---

### Post by cespinal on 2010-04-16
Has intentado bajarte el jacked y usarlo junto con audacity?

---

### Post by granjero on 2010-04-16
cespinal, que es el jacked, busqué en google y en synaptic y no se que es....

---

### Post by guillermolisi on 2010-04-16
> **cespinal said:**
> Has intentado bajarte el jacked y usarlo junto con audacity?
Jack no requiere del kernel RT (Real Time) ?

Igual Audacity deberia funcionar sin Jack.

---

### Post by granjero on 2010-04-17
tengo instalado jack pero no para de tirarme errores

probé con ardour también pero ese ni me deja arrancar... Alguna idea de lo que pueda ser?


salud!

---

### Post by granjero on 2010-04-18
el grabador de sonidos del sistema anda perfecto...

"mhWaveEdit" graba perfecto también, pero no me deja guardar en mp3.

logre que ardour arranque y grabe, pero no logro que reproduzca!

desinstalé audacity y volví a instalarlo pero sigue haciendo lo mismo.  

¿como se hace para desinstalar 100% una aplicación...

que se borren también los archivos de configuración y todo el resto de las cosas?

salud!

---

### Post by guillermolisi on 2010-04-18
Para desinstalar completamente un paquete, incluyendo los archivos de configuracion, via Synaptic, tenes que marcar el paquete con click derecho y elegir "Mark for Complete Removal" o lo que resulte de su traduccion (uso Ubuntu en Ingles).

---

### Post by granjero on 2010-04-18
eso fue lo que hice, y después lo reinstalé con ```
sudo apt-get install audacity
``` y me hace lo mismo....

cuando pongo grabar graba los primeros 3 segundos y despues se traba.....

me gustaría que funcione...

que puedo probar?


salud!

---

