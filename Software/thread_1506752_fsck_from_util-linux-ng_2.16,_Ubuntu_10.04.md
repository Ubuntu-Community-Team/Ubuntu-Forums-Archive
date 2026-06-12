---
title: "fsck from util-linux-ng 2.16, Ubuntu 10.04"
date: 2010-06-10
forum: Software
---

### Post by Sanctus119 on 2010-06-10
Hola
Hace poco instalé Ubuntu 10.04 en mi computador, un notebook Vaio VGN-NW215T. Al comienzo iba bastante bien, pero luego de un tiempo comenzó a pasar que cuando seleccionaba Ubuntu desde Grub (lo tengo compartido con Windows 7), el sistema se quedaba unos 15 segundos "pensando" antes de mostrar la ventana púrpura de carga de Ubuntu, y una vez que llegaba hasta aqui, se reiniciaba el computador. Intenté iniciar por modo de recuperación y se mostraba el siguiente mensaje antes de reiniciar:
fsck from util-linux-ng 2.17.2

Lo extraño es que a veces, luego de quedarse pensando esa línea, lograba iniciar el sistema. Otras veces llegaba hasta ahi y se reiniciaba, pero cada vez se ha hecho más dificil iniciar Ubuntu.

He leido distintas versiones sobre esto. Que es un bug no resuelto, que es un problema de compatibilidad con los drivers de virtualbox (uso virtualbox), pero desde dentro del sistema aparentemente no tengo problemas de paquetes rotos ni nada por el estilo, por lo que no se me ocurre que puede haber.

---

### Post by juancarlospaco on 2010-06-10
Chequeo de disco, 
fijate la utilidad de discos que te informa de la salud de tu disco.

:)

---

### Post by marcelo_bur on 2010-06-10
Hola. A mi me pasó con mi Hardy hace ya un tiempo. No se como se verá en tu note, en mi pc iniciaba un chequeo de rutina del disco cada vez que la prendia y luego de un ratito me tiraba toda una serie de datos donde también me pedia que ejecute "fsck". Durante un tiempo solucione el problema presionando escape cuando comenzaba el chequeo, hasta que aprendí como ejecutar correctamente fsck, que creo es el equivalente a ScanDisk de Window$, no se bien que hizo, creo que no repara los clusters dañados del disco, solo toma nota de cuales son para dejarlos en desuso, no soy tan entendido, el caso es que desde entonces, y por suerte, no tuve más problemas.
En definitiva, creo que como dice juancarlopaco se trata de un problema fisico en el disco y tendrás que ver la manera de ejecutar ese programa, que es el que soluciona el problema.
Saludos

---

### Post by Sanctus119 on 2010-06-10
Gracias por las respuestas estimados.

La utilidad de discos de Ubuntu me dice que los discos deben estar desmontados para analizarlos. ¿Debería usar un live cd para poder usar esta utilidad y reparar todo posible daño?. Igual es extraño considerando que este computador tiene poco más de 5 meses.

Aquí curiosamente no se hace un chequeo al estilo de scandisk. Al comienzo cuando Ubuntu estaba recién instalado, después de una cantidad de arranques, se hacía un scan que mostraba el porcentaje de avance y luego iniciaba el sistema. Ahora sólo aparece esa línea una o dos veces (una o dos, siempre varía), a veces se reinicia automaticamente y otras veces muestra un resultado de scan parcial de disco para luego continuar con el arranque. Es raro porque a veces arranca al primer intento, otras veces se reinicia una vez y luego todo normal, y otras veces ni con cinco reinicios se acaba el loop.

---

### Post by marcelo_bur on 2010-06-11
Lamentablemente lo que comentas está más allá de mis conocimientos. Espero que alguien más entendido en esto te pueda ayudar. Saludos y suerte.

---

### Post by guillermolisi on 2010-06-11
Asi es, para correr fsck sobre un disco/particion, la misma debe estar desmontada.
Si inicias la maquina con un LiveCD deberias poder correr fsck en consola/terminal de todas las particiones de los discos que estas usando.

Sugiero leer por lo menos el man (manual en linea de comando) de fsck antes de aplicarlo para evitar que el "remedio sea peor que la enfermedad".

---

### Post by juancarlospaco on 2010-06-11
**sudo touch /forcefsck && sudo reboot**

---

### Post by guillermolisi on 2010-06-11
> **juancarlospaco said:**
> **sudo touch /forcefsck && sudo reboot**
Amplio el telegrama de Juan Carlos: Con estos comandos, que se deben correr en una consola/terminal, se fuerza el fsck para el proximo inicio del sistema.

Gracias Juanca.

---

### Post by Sanctus119 on 2010-06-13
Viendo con detalle lo que salía antes de que el computador se reiniciara, me di cuenta que, aparentemente, el problema tiene que  ver con una partición Fat32 que uso como "mis documentos" entre windows y ubuntu.
Cuando cree esta partición la dejé como Fat32 y montada en /pablo (en la raiz del sistema). Hoy ,por Windows, cambié la partición a Ntfs pero resulta que ahora Ubuntu no inicia y queda pegado en la línea de que está chequeando una partición.
Más tarde recuperaré unos live cds que presté para ver desde ahi que está pasando, pero de momento no se por donde partir revisando. El archivo fstab en esta versión de Ubuntu es bastante más confuso a como era antes asi que no se me ocurre que otros archivos ver.

---

### Post by guillermolisi on 2010-06-13
Si tenes la entrada en /etc/fstab que monta esa particion, con solo adecuar el nuevo tipo de filesystem deberia volver a funcionar, es decir adecuar donde dice que es FAT a que diga NTFS con mas algun otro parametro si es que corresponde para NTFS.

---

### Post by Sanctus119 on 2010-06-13
> **guillermolisi said:**
> Si tenes la entrada en /etc/fstab que monta esa particion, con solo adecuar el nuevo tipo de filesystem deberia volver a funcionar, es decir adecuar donde dice que es FAT a que diga NTFS con mas algun otro parametro si es que corresponde para NTFS.

En fstab la última vez que revisé no habían entradas para las particiones que se habían configurado durante la instalación del sistema operativo. Si no hay una entrada ahi, donde más se podría configurar?

---

