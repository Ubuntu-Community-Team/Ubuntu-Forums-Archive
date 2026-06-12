---
title: "Armar un script para snapshots"
date: 2010-02-09
forum: Software
---

### Post by sergiom99 on 2010-02-09
Hola gente,
estaba tratando de armar un script para Ksnapshot, para que en un X intervalo capture imagenes y las guarde en archivos consecutivos.

Encontre este script [1]. Si ven el original, en el loop aparece un emoticon que yo lo interprete como que quiso poner i=i, puede ser que este mal.
```

#!/bin/bash

#set time between grabs
dcop ksnapshot-`pgrep -u $USER ksnapshot` interface setTime 1

# loop from 0 to 9
for ((i=0;i<10;i=i))

#grab a shot:
do dcop ksnapshot-`pgrep -u $USER ksnapshot` interface slotGrab

#save it to a numbered file:
dcop ksnapshot-`pgrep -u $USER ksnapshot` interface save ksnapshot-dcop-$i.png

#end of loop
done 

```

El asunto es que al correrlo me tira esta sucesion de errores hasta que lo corto:
```

sergio@kubuntu:~$ ./capturas.sh 
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!
ERROR: Couldn't attach to DCOP server!

```

Alguien tiene idea de como lograr esto?
En el manual de Ksnapshot algo dice del DCOP, asi que se debe poder, el asunto es que no se como programarlo. [2]

Gracias!!

[1] [http://forum.mandriva.com/viewtopic.php?p=60464&sid=5ba635b4faae469d129661e9203a7528](http://forum.mandriva.com/viewtopic.php?p=60464&sid=5ba635b4faae469d129661e9203a7528)
[2] [http://docs.kde.org/development/en/kdegraphics/ksnapshot/dcop.html](http://docs.kde.org/development/en/kdegraphics/ksnapshot/dcop.html)

---

### Post by alfplayer on 2010-02-09
Está ejecutándose el servidor DCOP ?

---

### Post by sergiom99 on 2010-02-10
que buena pregunta. Como lo sabria?
En el init.d solo tengo:
> 
$ l /etc/init.d/d*
-rwxr-xr-x 1 root root 4632 2009-01-27 12:37 /etc/init.d/dbus
-rwxr-xr-x 1 root root 8040 2009-03-05 14:31 /etc/init.d/dkms_autoinstaller
-rwxr-xr-x 1 root root 1235 2009-02-20 15:56 /etc/init.d/dns-clean


Gracias.

---

### Post by alfplayer on 2010-02-10
> **sergiom99 said:**
> que buena pregunta. Como lo sabria?
En el init.d solo tengo:


Gracias.

Estoy con karmic, recién lo inicié ejecutando dcopserver, y pude ver que está en ejecución con "ps aux". Nunca usé DCOP directamente, pero se puede probar si el script funciona así.

---

### Post by sergiom99 on 2010-02-10
Excelente!
lo arranque con dcopserver como dijiste.

Ahora me tira:
```
sergio@kubuntu:~$ ./capturas.sh 
object not accessible  
```

---

### Post by alfplayer on 2010-02-10
> **sergiom99 said:**
> Excelente!
lo arranque con dcopserver como dijiste.

Ahora me tira:
```
sergio@kubuntu:~$ ./capturas.sh 
object not accessible  
```

Si dcopserver fue iniciado con el usuario actual se puede probar con root o viceversa.

---

### Post by Hei Ku on 2010-02-10
DCOP no more, ya está out.

D-Bus es lo in.

---

### Post by alfplayer on 2010-02-10
> **Hei Ku said:**
> DCOP no more, ya está out.

D-Bus es lo in.

DCOP sigue funcionando?

---

### Post by sergiom99 on 2010-02-10
Gracias por las respuestas.
Pero en la documentacion de KDE dice que usa Dcop como D-bus interface. 
(A no ser que este desactualizado y no han puesto los nuevos comandos)

---

### Post by alfplayer on 2010-02-10
Por lo que se D-Bus **reemplaza** a DCOP desde KDE 4, pero sería bueno saber si la funcionalidad de DCOP sigue estando disponible.

---

### Post by Hei Ku on 2010-02-10
dbus es la evolucion de dcop, pero es extremadamente distinto como para que pueda haber unha interfaz. 
La guia para portar de dcop a dbus dice basicamente que te la aguantes y lo hagas a mano. Practicamente remite a los dichos del Diego. :D

Para ver la interfaz expuesta por dbus podes usar kdbus o qdbusviewer.

Los comandos son del estilo:
```

dbus-send --dest=org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.saveCurrentSession

```

---

### Post by sergiom99 on 2010-02-10
uh! tremendo entonces.
se acaba de pinchar el globo de hacer un script para hacer capturas a intervalos regulares.

O buscare otra alternativa al Ksnapshot para usarlo desde bash.

Gracias Hei Ku y alfplayer por los aportes.

Si logro armar algo lo ire posteando y si a alguien se le ocurre algo acepto sugerencias.

---

### Post by sergiom99 on 2010-02-11
Encontre otra manera de hacer un script para snapshots con scrot [1]

Alguien me puede dar una mano para reformar el script original que corra en un loop cada 2 segundos?

Quiero salvarlas con un formato de nombre `date +%d-%m-%y_%H:%M:%S`_sreenshot.png para que no haya problemas con repeticiones.

Hasta ahora tengo algo asi
```

#!/bin/bash
scrot -s -b -e 'mv $f ~/Pictures/scrot/`date +%d-%m-%y_%H:%M:%S`_sreenshot.png'

```

Me falta loopearlo.

Gracias!

[1] [http://www.kubuntu-es.org/wiki/graficos/howto-hacer-capturas-pantalla-usando-scrot-screen-shot](http://www.kubuntu-es.org/wiki/graficos/howto-hacer-capturas-pantalla-usando-scrot-screen-shot)

---

### Post by alfplayer on 2010-02-11
> **sergiom99 said:**
> Encontre otra manera de hacer un script para snapshots con scrot [1]

Alguien me puede dar una mano para reformar el script original que corra en un loop cada 2 segundos?

Quiero salvarlas con un formato de nombre `date +%d-%m-%y_%H:%M:%S`_sreenshot.png para que no haya problemas con repeticiones.

Hasta ahora tengo algo asi
```

#!/bin/bash
scrot -s -b -e 'mv $f ~/Pictures/scrot/`date +%d-%m-%y_%H:%M:%S`_sreenshot.png'

```

Me falta loopearlo.

Gracias!

[1] [http://www.kubuntu-es.org/wiki/graficos/howto-hacer-capturas-pantalla-usando-scrot-screen-shot](http://www.kubuntu-es.org/wiki/graficos/howto-hacer-capturas-pantalla-usando-scrot-screen-shot)

Se puede usar el comando watch con scrot en lugar de un script.

---

### Post by sergiom99 on 2010-02-11
Excelente!
Ahi quedo algo parecido a lo que yo queria.

Gracias!

---

