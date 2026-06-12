---
title: "Problema al iniciar"
date: 2010-08-07
forum: Software
---

### Post by dam1977 on 2010-08-07
Tengo instalado Ubuntu 10.04 y Win XP en una máquina con Core 2 Duo y 3 gigas de RAM. Disco duro de 500 gigas. Hace unos días que no inicia el Grub. Se queda en una pantalla negra con el prompt de grub. pero no funciona ninguno de los comandos de grub que averigué (ni boot, ni exit, nada). Arrancando con el CD de Ubuntu, cuando voy a Lugares veo las dos particiones (Win y Ubuntu) pero si quiero montar la partición de Ubuntu (aunque sea para copiar todas las cosas que tengo ahi) me aparece el siguiente mensaje:

Error mounting: wrong fs type, bad option, bad superblock on /dev/sda5
Missing codepage or helper program or other error in some cases useful info is found in syslog - try dmesg / tail or so

deduzco que hay un problema en la partición donde está Ubuntu (es la /dev/sda5) pero no acierto a entender cual es el problema ni como corregirlo. Desinstalé por completo el Grub y lo volví a instalar y no hay caso, sigue igual.

---

### Post by alfplayer on 2010-08-07
Típico error después de un apagón. Hay otros en este foro con el mismo problema, la solución sería ejecutar *fsck* a esa partición, que se puede hacer desde el live cd.

---

### Post by dam1977 on 2010-08-08
Solucionado con Gparted. Verificar y reparar. Y chau picho!!! Todo recuperado y tal como estaba antes del colapso inexplicable (quizas haya sido un corte o algo así)

---

