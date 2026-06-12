---
title: "Tareas programadas, presentaciónes Impress, scripts. [AYUDA]"
date: 2010-07-10
forum: Software
---

### Post by granjero on 2010-07-10
Hola comunidad. Tengo una pc que va a ir dentro de una vitrina mostrando presentaciones realizadas con el Impress de OpenOffice, la idea es encenderla y con el visor de escritorios maejarla.

Con eso no hay problema, ya lo manejo desde cualquier pc de la red sin problema pero cuando quiero arrancar a programar las tareas con gnome-schedule me está dando dolores de cabeza.

Hice dos presentaciones que se repiten al terminar. Con dos imágenes cada una.

/home/jm/Escritorio/art.odp
/home/jm/Escritorio/mutante.odp

hice dos scripts para ejecutarlas:
art.sh
```
#! /bin/bash
soffice -show /home/jm/Escritorio/art.odp
```

mutante.sh
```
#! /bin/bash
soffice -show /home/jm/Escritorio/mutante.odp
```

Cuando los pongo en el gnome-shcedule y apreto el botón de prueba los ejecuta y arrancan.

Pero cuando los pongo para que vallan solitos no andan.

Qué es lo que estoy pasando por alto????

gracias de antemano.

salud!

---

### Post by juancarlospaco on 2010-07-10
#!/bin/bash
sh -e "soffice -show /home/jm/Escritorio/mutante.odp &"

sino tambien:

#!/bin/bash
xdg-open soffice -show /home/jm/Escritorio/mutante.odp &


Deberia andar... fijateque los .sh tengan permisos de ejecucion.

---

### Post by granjero on 2010-07-13
gracias juancarlospaco, pero no me fue bien con lo que me pasaste.

te cuento:

con el primer scritp que me pasaste sale esto


```
sh: Can't open soffice -show /home/jm/Escritorio/art.odp &
Press ENTER to continue and close this window.

```

con el segundo me da esto


```
Press ENTER to continue and close this window.
xdg-open: unexpected option '-show'
Try 'xdg-open --help' for more information.
```

esto es siempre apretando el botón de prueba, porque si lo dejo andando no pasa nada nunca. 

probé de todas las formas posibles:

con el script, con el comando directo , en repetición, probé de todo y nada.

no le engancho la mano


ahí los permisos de los scripts


```
jm@blanquita:~/scripts$ ls -l
total 8
-rwxr-xr-x 1 jm jm 65 2010-07-13 00:24 art.sh
-rwxr-xr-x 1 jm jm 69 2010-07-13 01:04 mutante.sh
```


salud!

---

### Post by granjero on 2010-07-13
leyendo y leyendo encontré que hay un programa muy similar "Alarm-clock" que está en los repositorios.

logré hacerlos andar pero ahora necesito una manito con los scripts ya que antes de arrancar a reproducir las presentaciones tengo que cerrar la que se abrió antes.

Voy a leer sobre el comando kill y cuando logre hacerlo andar posteo la solución y doy por [SOLVED] el asunto!

salud y gracias! ;)

---

### Post by alfplayer on 2010-07-14
Puede servir el comando killall.

---

### Post by granjero on 2010-07-18
gracias alfplayer. 
si desde una terminal escribo killall soffice.bin me cierra el openoffice

pero en el script pongo

#! /bin/bash
killall soffice.bin
soffice -show /home/jm/Escritorio/art.opd

y cuando lo pongo en las tareas, llega la hora de ejecutarse, desaparece la línea como si se hubiera ejecutado pero no pasa nada de nada.

alguna idea?

la data que encontré sobre scripts es toda muy avanzada para mi....

salud!

---

### Post by alfplayer on 2010-07-18
> **granjero said:**
> gracias alfplayer. 
si desde una terminal escribo killall soffice.bin me cierra el openoffice

pero en el script pongo

#! /bin/bash
killall soffice.bin
soffice -show /home/jm/Escritorio/art.opd

y cuando lo pongo en las tareas, llega la hora de ejecutarse, desaparece la línea como si se hubiera ejecutado pero no pasa nada de nada.

alguna idea?

la data que encontré sobre scripts es toda muy avanzada para mi....

salud!

El script funciona desde terminal?

---

