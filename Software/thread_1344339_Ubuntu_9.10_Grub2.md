---
title: "Ubuntu 9.10 Grub2"
date: 2009-12-02
forum: Software
---

### Post by NickCis on 2009-12-02
Hola, acabo de instalar ubuntu 9.10, y me veo con problemas con el grub. Ya que mi computadora es vieja, para que apague, nececito agregarle la opcion "ACPI=FORCE" al boot. Esto lo hacia modificando el menu del grub. El problema es que ahora no lo puedo encontrar =S.

Como puedo arreglar este problema?.

Saludos

---

### Post by Hernán-Amaya on 2009-12-02
Por lo que tengo entendido el GRUB2 tiene otros archivos de configuración. Fijate si te da una mano este link [http://www.guia-ubuntu.org/index.php?title=Grub](http://www.guia-ubuntu.org/index.php?title=Grub)

---

### Post by NickCis on 2009-12-03
me sirbio, muchas gracias.

Termine modificando el archivo "/boot/grub/grub.cfg", busqe la parte qe estaba el ubuntu y le agregue el "acpi=force".

No se si lo qe hice esta bien, por qe parece qe te dice qe esta terminantemente prohibido modificar ese archivo, si no qe tenes qe modificar no se archivo y hacer qe lo cree el grub (con eso de update)... Pero, bueno mi solucion pareciese ser mas rapida y sin ningun daño colateral (va eso espero xD).

Saludos.

---

### Post by alfplayer on 2009-12-04
> **NickCis said:**
> me sirbio, muchas gracias.

Termine modificando el archivo "/boot/grub/grub.cfg", busqe la parte qe estaba el ubuntu y le agregue el "acpi=force".

No se si lo qe hice esta bien, por qe parece qe te dice qe esta terminantemente prohibido modificar ese archivo, si no qe tenes qe modificar no se archivo y hacer qe lo cree el grub (con eso de update)... Pero, bueno mi solucion pareciese ser mas rapida y sin ningun daño colateral (va eso espero xD).

Saludos.

Ese archivo se supone que no es para modificar por el usuario editándolo directamente. Una actualización de ubuntu puede revertir el cambio realizado.

---

### Post by NickCis on 2009-12-05
Finalmente pude resolver mi problema, modificando el "/etc/default/grub".
En la linea: GRUB_CMDLINE_LINUX_DEFAULT=" ... "
Agregue la opcion: "acpi=force" y dsp del grub-update problema resuelto =P
Saludos.

---

