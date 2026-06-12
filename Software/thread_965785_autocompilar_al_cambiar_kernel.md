---
title: "autocompilar al cambiar kernel?"
date: 2008-10-31
forum: Software
---

### Post by z37a on 2008-10-31
Gente una consulta, tengo en mi laptop una placa Wifi Atheros 5007, como se sabe esta placa mal parida no funciona bien, por lo cual deboi compilar los madwifi para que funcione, el tema es que cada vez que cambio el kernel, va se actualiza, tengo que recompilar los madwifi, hasta ahora lo solucione poniendo un script para que solo ejecute un comando, pero tocando la laptop de un amigo vi que con la placa de video de el se podia configurar un script para que al actualizarse el kernel se autocompile el driver de video automaticamente, hay alguna forma de hacer esto con el madwifi(por que no funciono hacer lo mismo)?

---

### Post by sdennie on 2008-10-31
Si, se puede sin problema.  Hice una guia (en ingles) para hacerlo por los drivers de nvidia: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).  Despues de leer eso vas a entender pero, tambien tengo otros scripts in /etc/kernel/postinst.d.  Son ejemplos pero capaz que te ayudan:

Recompilar el driver de VirtualBox (PUEL):

```

#!/bin/bash

echo "Building VirtualBox driver for $1" >&2
cd /usr/share/virtualbox/src
make clean 2>&1 > /dev/null
make install KERN_DIR=/lib/modules/$1/build KERN_INCL=/lib/modules/$1/build MODULE_DIR=/lib/modules/$1/misc 2>&1 > /dev/null

depmod -a $1

```

Recompilar el driver de ALSA (despues de hacer un link de /usr/src/alsa a los drivers que queres usar (solo el driver de hda-intel en este caso)):

```

#!/bin/bash

echo "Building ALSA drivers for $1" >&2
cd /usr/src/alsa
make clean 2>&1 > /dev/null

./configure --with-kernel=/lib/modules/$1/build --with-cards=hda-intel 2>&1

make install 2>&1 > /dev/null

exit 0

```

Yo siempre estoy compilando kernels nuevos y tengo un monton de scripts asi.  Literalmente puedo decir "dpkg -i linux*-new-kernel-name*.deb && reboot" y todo funciona perfecto despues de re-iniciar porque los scripts andan con el dpkg -i (o apt-get o cualquier cosa).

Si necesitas mas ayuda, mandame los comandos que usas para compilar el driver y te mando el script para hacerlo.

---

### Post by z37a on 2008-11-02
Gracias pro los scripts!!!!

Igual te cuento, la nueva feature del 8.10 que hicieron con dell anda de 10, actualize el kernel de la laptop y no necesite recompilar el driver madwifi, espero esta suceda si sale un nuevo kernel tambien(por que pro ahoira solo lo probe con el update del kernel)

---

