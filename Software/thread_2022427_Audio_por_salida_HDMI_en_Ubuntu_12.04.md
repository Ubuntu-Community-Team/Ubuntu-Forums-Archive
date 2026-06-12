---
title: "Audio por salida HDMI en Ubuntu 12.04"
date: 2012-07-10
forum: Software
---

### Post by DrKenobi on 2012-07-10
Hola,

Yo quiero usar la salida HDMI en Ubuntu, pero no logro tener sonido.
Tengo una placa AMD RadeonTM HD 6570M Graphics.
Intente con lo siguiente, pero no pude hacerlo funcionar:

sudo gedit /etc/default/grub

Se abre un archivo, modifico la linea:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

con:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

Guardo, luego:

sudo update-grub

Reunicio PC

---

