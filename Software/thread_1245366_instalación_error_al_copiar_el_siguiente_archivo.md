---
title: "instalación: error al copiar el siguiente archivo"
date: 2009-08-20
forum: Software
---

### Post by nachocuervo on 2009-08-20
Ayuda!!   no puedo completar la instalación WUBI de ubuntu-8.04.2-desktop-i386 !!
Intento instalarlo dentro de Windows y me sale error. Ya intenté muchas veces, voy a describir los pasos que hice exactamente la última vez:
:-\"Primer descargué la imágen "ubuntu-8.04.2-desktop-i386.iso" y generé un md5 que dio 
correcto con lo que dice en internet.
:-\"Desfragmenté el disco D: (de datos) que tiene 6 GB de espacio libre apróx.
:-\"Monte una imagen de disco con MagicDisc y verifiqué la imágen con "md5summer".
:-\"autorun: "instalar dentro de windows", completo los datos, instalo con 4GB, y elijo "reiniciaré yo más tarde el equipo"
:-\"en D:/ubuntu/install/installation.ISO , noté que se crea una copia del disco de instalación, y entonces le hice un md5summary para comprobar la integridad (porque en otro post comenté que tube muchos problemas con el archivo "filesystem.squashfs" con el disco de instalación, y veo que no da correcto. entonces copio el ISO original y renombro "installation.ISO". ¡Quiero aclarar que este paso polémico lo hice después de probar infinidad de veces directamente sin poder completar nunca la instalación!
:-\"reinicio la pc, en el menú de arranque elijo "ubuntu" y espero...
:-\"parece todo normal, se llena la barra...
!!!:-\"inicia la instalación, configuracion de sistema, particionado, etc, espero...   y cuando dice instalando sistema en el 39% tira :
> Error al copiar 
el siguiente archivo no coincide con cu copia de origen en el CD/DVD 
/target/usr/lib/mono/gde/mono.security/ 2.0.0.0_0738eb9F132ed756/mono.security.dll
"cancel"  "retry" "skip"
Pongo skip y en 52%:
> Error al copiar 
El instalador encontró error al copiar los archivos al disco duro
[ERRNO5] input/output errorpongo skip y se finaliza va el carel de instalación q iba por 52%  y se escucha el sonido de ingreso a ubuntu y aparece el escritorio completo, y aparentemente anda, solo que es evidente q no termino la instalación y si reinicio la pc ya no puedo ingresar a ubuntu de nuevo.

El ISO esta corroborado y descargado x diferentes medios, torrent y firefox. Probé instalar desde un CD en vez de una imágen de disco y tampoco. El LiveCD anda de primera.
No sé de qué se trata el problema, yo creo que puede ser el disco duro, pero la verdad no sé, a ver si alguien es capaz de decirme si puede ser eso. 
Les dejo los datos de un informe de AIDA32 del disco q consideré mas reelevantes ... 
> Es una laptop con Win Xp HomeEdition SP2, 1GB de RAM, intel Pentium 1,73 Ghz
Dos particiones:
C: (VAIO)    Disco locale    NTFS    54A5-8EF0    33385 MB    707 MB    2 %
D: (VAIO)    Disco locale    NTFS    2CAF-8D61    35777 MB    1059 MB    3 %
(Tener en cuenta que ya está ocupado el lugar de instalacion de wubi en D: )
y  el informe completo de Hard por si necesitan más lo adjunto


si  alguien me puede ayudar se lo agradezco muchiiiiisimooo!!!

---

