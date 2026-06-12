---
title: "Presentación con duda :)"
date: 2008-10-01
forum: Software
---

### Post by Pantroc on 2008-10-01
Hola señores les doy un abrazo a todos y me presento….

Quiero hacer una pregunta que seguramente ustedes que son ubunteros de alma saben la respuesta.

Les cuento.
Ya anteriormente instalé linux, pero lo había instalado como sistema operativo único, era el viejo y una masa suse 9.0 que me dio muchas alegrías y anda de 10.
Llegó a mis manos la distribución de ubuntu 7.10 el live cd de instalación. OK todo bien tengo en este momento el sistema operativo de el señor Gate, no lo quiero nombrar así no se enojan ni les traigo alguna desgracia en el foro J

Que pasó? Es simple tengo un disco particionado de la siguiente manera:

C: / 20 NTFS gigas para el SO del señor Gate.
D: / 16 gigas NTFS (vacío) mi idea es instalar el ubuntu acá
E: / 20 gigas NTFS de respaldo
F: / 20 gigas NTFS varios 

OK todo de 10……. por si preguntan tengo un p4 de 3 gigas Prescott 1 giga de memoria en dual Channel ocz  mother de ****** asrock chipset Intel.

Lo que me pasa es que cuando, tengo que particionar, no me ve o no me reconoce las particiones ya echar que les mencioné anteriormente, me da la única opción de paraticionar utilizando todo el disco ósea los 80 gigas.

Y lo que quiero yo es instalarlo en D:

Alguien sabe como puedo hacer para que me vea las particiones y me deje instalarlo en d: y así no pierdo nada 


Saludos y mil disculpas y gracias a los que se tomaron la delicadeza de leer este post.

---

### Post by Mauro22 on 2008-10-01
Hola y Bienvenido!


Pregunta: Durante el asistente de instalacion, elegiste particionado automatico o manual?


Vas a tener que hacer 3 particiones:

1 particion para el S.O. con punto de montaje / y formato ext3
1 particion para los datos con punto de montaje /home y formato ext3
1 particion formato swap para intercambio (se calcula RAM x 2)

---

### Post by Pantroc on 2008-10-01
HUaaauuuuu gracias por responder asi tan rapido 

te cuento Mauro22

cuando llego a la parte de particionado tengo las 3 opciones clasicas 

GUIADO *
Utilisando todo el disco 80 gigas *

Manual

que pasa la opción que me da es guiado utilisando todo el disco, no me deja desmarcar utilisando todo  el disco, osea quedan las dos marcadas con el punto rojo......

y cuando pongo manual no me muestra ninguna particion de las que están echas 

lo loco es que en el entorno grafico de el live cd antes de empesar la instalción es que si veo todas las particiones ( raro)

---

### Post by Mauro22 on 2008-10-01
Si no te muestra nada, se me ocurre:

Tenes mas de un disco (aunque por tu post no es asi) ??


Al principio pense que por ahi no te esta reconociendo el disco, pero al darte guiado de 80GB, es obvio que te lo reconoce.


A ver si alguien se le ocurre otra cosa...

---

### Post by leo_rockway on 2008-10-01
¡Bienvenido!

Fijate si podés particionar con otro programa. Ubuntu trae el GParted (creo que en Ubuntu en el menú de Gnome aparece como Gestor de particiones o algo así).
A mi me gusta más GParted que el particionador del instalador...

Si no, usá el Acronis del Hiren's Boot CD: no es Software Libre pero es por una buena causa.
El otro día Faktor me presentó este programa y me sacó de un apuro con un HD rebelde que no se quería particionar.

---

