---
title: "problemas con arranque de ubuntu 9.10"
date: 2010-03-12
forum: Software
---

### Post by naldocz on 2010-03-12
Hola a toda la comunidad..
ando con algun problemita que no se como solucionarlo y espero la gran ayuda de ustedes.
les cuento que hace unas semanas installe en mi pc sin particion de disco, la version 9.10 de ubuntu y que hasta el momento funcionaba de maravilla, si pero de repente no comenzo a iniciarse directamente en ubuntu sino que me da para la eleccion de inicializar desde ubuntu, linux 2.6.31-20-generic y versiones anteriores con sus respectivos recovery mode y luego el memory test.
cuando doy para que inicie en la primera opcion ubuntu linux 2.6.32-20 generic, me lleva a la siguiente: 

Filesystem check failed
a maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@users- desktop:

y ya no va adelante.
con la desesperacion e intentado con el cd del supergrub y con el livecd de ubuntu 9.10 para re instalarlo pero sin ningun resultado... es como si no los leyera..
entonces les pido una gran ayuda para salir de esta que no entiendo por que de repente paso esto.
gracias y a la espera..

---

### Post by Silop on 2010-03-13
lo que pasa es que actualizaste el kernell y eso es lo que estas viendo que aparecen mas cantidad de opciones en tu menu grub, dices que vaya en una, pero las demas andan?, puede que solo sea un error de actualizacion... proba las otras... y si funciona alguna, actualiza todo desde ahi nuevamente..

---

### Post by guillermolisi on 2010-03-13
Para mi hay algun problema en la estructura de archivos del disco, que puede ser tanto de soft como de hard, que hace que el fsck (File System Check) no pueda hacer su tarea y requiere de la intervencion humana.

El fsck se dispara despues de cierta cantidad de veces que las particiones se montan o cuando al inicio detecta problemas (archivos mal cerrados/corruptos o similar).

---

