---
title: "Problema con el dual boot"
date: 2010-07-05
forum: Software
---

### Post by LianRome on 2010-07-05
Hola
yo tengo dos discos cada uno con su SO (Prioridad de inicio Ubuntu y en el otro XP). Durante la actualización del 9.10 a Lucid me apareció una pregunta para escoger las opciones que debería mostrarme el GRUB y estaban todas las particiones. Había un consejito escrito que decía: Si no estás muy seguro de cuáles escoger, elige todas. Eso hice y en los detalles de la actualización vi que aparecían algunos errores.
Ahora enciendo mi máquina y el GRUB (versión 1.98) me da a elegir entre los distintos núcleos de Ubuntu y el /dev/sdb2 del XP, aunque si elijo esta opción no carga nunca.
Entrando al Setup le doy prioridad de booteo al disco rígido en el que está XP, y lo raro es que no va directamente, sino que también aparece el GRUB...
A Ubuntu entro perfecto y hasta puedo ver los archivos del XP. El problema es que no puedo iniciar en Wdows.
Les agradezco por su ayuda y ¡saludos!

---

### Post by leonardomdq on 2010-07-06
Para recuperar el GRUB aca tenes una guia que te explica como hacerlo [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by LianRome on 2010-07-06
¡Gracias Leonardo! yo había visto ese tutorial, lo que pasa es que consideraba que no había perdido el GRUB :confused: porque me seguía apareciendo ;)
Bueno entonces le doy para adelante con eso. Disculpá esta pregunta: sigo los pasos del Grub 1, ¿no? Porque la versión que tengo es 1.98.
¡Abrazo!

---

### Post by alfplayer on 2010-07-06
Los que son "casi 2" son Grub 2.

---

### Post by LianRome on 2010-07-17
¡Gracias!
Bueno, mirá, detallo los pasos que hice:
Como ocurría que con frecuencia desaparecía el sonido y también no reconocía la compactera, lo que hice fue una nueva instalación del 10.04 con el CD de instalación desde cero, es decir "pisando todo". Antes la había hecho actualizando el 9.10.
El problema del thread aún continuaba (no puedo iniciar Wdows), así que seguí los pasos de [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB) referidos al Grub 2, usando como LiveCD el de 10.04.
Luego de este paso:
```
# grub-install --recheck /dev/sda
```

obtuve lo siguiente:
```
/proc/devices: fopen failed: no such file or directory
```
creo que esta línea se repitió 3 veces más y luego:

```
Is device mapper driver missing from kernel?
```
```
/proc/devices: fopen failed: no such file or directory
```
(se repitió más veces que antes)
```
Failed to setup list of device-mapper major numbers
```
```
/proc/devices: fopen failed: no such file or directory
```
también muchas veces

```
Installation fineshed. No error reported
```

Ahí todo concluyó. Cuando quise cerrar la terminal me indicó que tenía un proceso ejecutándose y tuve que ponerle "Cancelar" para poder cerrarla.

Reincié y lamentablemente todo continuó como antes.

¿Tuvo que ver la nueva instalación?
Cuando en el link mencionado dice "Ahora, monta el resto de los dispositivos:" ¿tengo que escribir literalmente lo del instructivo o debía haber escrito sdb1, etc.? (según entiendo, es en sdb1 que tengo el arranque de Wdows).

¡Muchas gracias por su ayuda y saludos!

---

### Post by alfplayer on 2010-07-17
El comando grub-install --recheck fue ejecutado como root ? (eso indica el símbolo numeral).

El comando "para montar los dispositivos" debe ser escrito sin modificar.

---

### Post by LianRome on 2010-07-17
Sí, creo que lo escribí como root. Antes de escribirlo le di esta orden:
$ sudo chroot /mnt

y entonces apareció el #
Es lo que me preguntás, ¿no?

---

### Post by alfplayer on 2010-07-17
> **LianRome said:**
> Sí, creo que lo escribí como root. Antes de escribirlo le di esta orden:
$ sudo chroot /mnt

y entonces apareció el #
Es lo que me preguntás, ¿no?

Sí, era eso.

Leyendo bien el hilo, si no bootea windows con prioridad en BIOS sugiere un problema con el cargador de booteo de windows. Recomiendo solucionar eso primero.

---

### Post by LianRome on 2010-07-17
Sí, a mí me pareció extraño que tampoco arrancara en Wdows dándole prioridad en el BIOS.
Lo raro es que esto comenzó luego de la actualización a Lucid, por lo que parecería un tema relacionado con el soft.
¿Me sugerís que investigue en internet con este criterio: "cargador booteo windows"?
¡Gracias por tu ayuda!

---

### Post by alfplayer on 2010-07-17
> **LianRome said:**
> Sí, a mí me pareció extraño que tampoco arrancara en Wdows dándole prioridad en el BIOS.
Lo raro es que esto comenzó luego de la actualización a Lucid, por lo que parecería un tema relacionado con el soft.
¿Me sugerís que investigue en internet con este criterio: "cargador booteo windows"?
¡Gracias por tu ayuda!

Sí, esa búsqueda puede ayudar, *recuperación cargador booteo windows xp*. En este foro probablemente hay algún tema viejo con esa información.

---

### Post by LianRome on 2010-07-17
Gracias, voy a buscar.

---

### Post by biale on 2010-07-23
Es muy posible que la causa del problema haya sido el bug 576724. Hoy apareció el fix:

 * Only offer partitions containing /, /boot, or /boot/grub for
    grub-install; installing to other partitions may have harmful effects
    such as making Windows unbootable, and installing GRUB to every single
    partition is likely to result in confusion anyway (LP: #576724).

---

### Post by LianRome on 2010-07-24
Gracias Biale, me parece que sí, que ¡va por ahí!
Estuve leyendo en [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724) y luego en [http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/lucid/grub2/lucid/revision/1973](http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/lucid/grub2/lucid/revision/1973) que es adonde está lo que vos transcribís.
Entiendo que están proponiendo una solución al consejito que provoca el error: "si no sabe cuál elegir, elija todas", como para que no ocurra más.

Lo que pasa es que no capto bien qué tengo que hacer yo para solucionarlo. Por ahí sea como dice aquí: [http://ubuntuforums.org/showthread.php?p=9257870#post9257870](http://ubuntuforums.org/showthread.php?p=9257870#post9257870) ¿Sigo estos pasos? ¿Cómo me doy cuenta si yo también tengo mezclados el GRUB Antiguo y el GRUB2?
¡Muchas gracias!

---

### Post by biale on 2010-07-24
Si entendí bien el problema pasaría por una mala instalación del grub en la partición y no en el MBR del disco. A los efectos prácticos "habría" que usar un CD de Windows, y en modo de manteninimiento (si no recuerdo mal) los comandos eran "fixmbr" y fixboot" (googlea con eso si es para XP)

Asegurate de apuntar bien al disco por BIOS. Y trata de tener a mano Live CD, supergrub disk, (mejor) desconectar disco de Ubuntu y lo que sea.

---

### Post by LianRome on 2010-08-13
OK, biale, gracias. Voy a avanzar así como me aconsejás. Ya estuve en [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
y anduve viendo fixmbr, fixboot y map.
Voy a arrancar con el cd de Windows. Cuando decís "apuntar al disco por BIOS" ¿es darle prioridad de booteo al que tiene Windows?
También encontré esto que no sé si te parece útil:
[http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)
[http://www.supergrubdisk.org/wiki/WindowsRefusesToBoot](http://www.supergrubdisk.org/wiki/WindowsRefusesToBoot)

Te consulto TODO porque como no la tengo muy clara me pierdo algunas cuestiones. Como siempre, muchas gracias.

---

### Post by LianRome on 2010-08-13
Bueno, tengo una novedad. Le di prioridad de booteo al disco en el que tengo Windows y apareció esto:
```
error: no such device: 26c7efda-5b88-470f-826c-630dab6035ff.
grub rescue>

```y queda el cursor titilando al lado.

Para seguir con los pasos, apagué y desconecté el disco en el que tengo Ubuntu y pasó lo mismo.

¿Sigo con los mismos pasos? Desde ya muy agradecido de antemano por la ayuda. ¡Saludos!

---

### Post by biale on 2010-08-14
En ese mensaje el grub te dice "arranque mi fase en el MBR y necesito lo que se encuentra en la partición ...35ff". Ningun problema.

Cuando arranques desde el CD de instalación de Windows, ese mensaje no va a aparecer. Desde la consola DOS de WXP reparas el arranque de WXP.  Y no hay riesgo con Ubuntu porque su disco esta desconectado.

Ahora WXP debería poder arrancar "por BIOS" y también con el supergrub disk. Vale la pena probarlo.

Volve a conectar el Disco de Ubuntu y ya con los dos discos arrancas desde el disco de Ubuntu. Si ahora Windows no arranca desde alli (y lo hacia por BIOS) hay que tocar las definiciones de grub para el arranque de WXP.

Atención que al menos uno de los tutoriales es para Grub legacy. Para este caso los conceptos sirven, pero los detalles de la sintáxis del Grub han cambiado.

---

### Post by LianRome on 2010-08-26
¡Grande biale! Detallo lo que hice:
- Desconecté el disco en el que tengo instalado Ubuntu
- Inicié con el CD de instalación de Windows
- En la consola apreté ENTER cuando me pidió contraseña de Administrador y pude entrar.
- escribí "fixboot" y le confirmé con "s" (sí) cuando me preguntó si lo quería hacer.
- salí de la consola para reiniciar

Acá me decepcioné un poco porque me tiró lo mismo que antes: no such device: 26c7efda-5b88-470f-826c-630dab6035ff.

Pero aún no había conectado el disco con Ubuntu nuevamente...
Cuando lo conecté y el GRUB me dio a elegir probé entrar en Windows ¡y entró!
Así que te estoy muy agradecido. ¡Saludos!

---

