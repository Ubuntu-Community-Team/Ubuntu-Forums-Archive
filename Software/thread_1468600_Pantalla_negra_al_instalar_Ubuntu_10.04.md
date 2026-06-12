---
title: "Pantalla negra al instalar Ubuntu 10.04"
date: 2010-05-01
forum: Software
---

### Post by cezario on 2010-05-01
Tengo un toshiba satellite A505-S6033, Baje la versión de 64bits desktop me sale el menú de instalación y cuando le doy instalar se queda funcionando pero la pantalla en negro, cuando le di probar la versión escuche el audio cuando inicio, pero igual la pantalla en negro, supongo que es porque no reconoce la tarjeta de vídeo.... que puedo hacer... leí que instalar en modo gráfico seguro pero no encontré la opción,... llevo todo el mes esperando que saliera para instalarlo :( ayuda... y gracias :)
P.D. Tarjeta de Video: NVIDIA GeForce 310M, La laptop solo tiene el windows 7

---

### Post by alfplayer on 2010-05-01
Es con F4 :

---

### Post by cezario on 2010-05-01
pero no me aparece la opcion solo la de los controladores y la oem a que se puede deber esto ?

---

### Post by alonso1970 on 2010-05-01
Instalé bien el Ubuntu 8, 9 y 10 pero cuando entro al sistema me sale la pantalla de los "propietarios de driver" y me señala específicamente mi tarjeta de video Nvidia TNT64 y me solicita "activarlo".
La primera vez lo hice en las 3 versiones de instalación (creyendo que iba a ser mejor en cada actualización) pero después de eso solo me carga una pantalla negra y me deja "congelada" la computadora.
No se cómo hacer para que esto no me pase más... Soy NOVISIMO en UBUNTU y no se cómo actualizar controladores.
Lo malo de no hacer esto, es que la resolución de la pantalla no es la que quiero o necesito si dejo esta opción sin activar.

Desde que salió la versión 8.1 estoy intentando resolver esto...

---

### Post by cezario on 2010-05-02
hola que tal, bueno pues les cuento mi anécdota... primero  instale el ubuntu 9.10 ese si me dejo en modo normal ni siquiera  necesite modo gráfico seguro (esa versión si lo tiene utilizando F4),  una vez instalado no quiso entrar en modo gráfico por un error  USB usb 1-1: device not acepting address 2 Error -110
En modo de recuperación lo actualice 
 sudo apt-get upgrade
 al reiniciar seguía con el mismo error del usb pero me dejo entrar en  low-grafics algo así, baje e instale los drivers de NVIDIA pero no  funciono, entonces actualice a ubuntu 10.04 desde el Gestor de  Actualizaciones esperando que todo se resolviera, se instalo y todo  seguía igual solo que ya tenia la versión 10.04 pero no me dejaba  entrar, entonces instale los drivers de NVIDIA y me dejo entrar en  low-grafics de nuevo, pero seguía con lo de la usb, busque en google y  me encontré que agregando pci=noacpi en el archivo del grub en una linea  que dice GRUB_CMDLINE_LINUX_DEFAULT
 en 
 sudo $ gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"

sudo $ update-grub
 eso soluciono los usb y luego en administración en controladores de  hardware instale el driver de NVIDIA pero aun se ve mal la resolución y  no tiene efectos seguiré intentando...

---

