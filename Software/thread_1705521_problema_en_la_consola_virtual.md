---
title: "problema en la consola virtual"
date: 2011-03-12
forum: Software
---

### Post by tio lucas on 2011-03-12
Hola muchachos, les escribo desde el otro lado de la cordillera. Resulta que tengo un problema con mi notebook. Al salir del entorno gráfico y pasar a las consolas virtuales, resulta que no alcanzo a ver toda la pantalla. No sé si alguno le ha pasado esto. Intenté arreglarlo desactivando el splash, pero no resultó. Leyendo por ahí me enteré que hay unos modos GFX, pero no entendí de que se trata. Me parece que han cambiado las cosas, porque en mis tiempos se cambiaba con vga=791. Si me pueden dar algún dato sobre esto también es bienvenido.
Mi máquina es un packard bell f7340 y tiene Ubuntu 10.04.

---

### Post by alarme on 2011-03-12
Hi,
try this:

edit /etc/default/grub

replace:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

with

GRUB_CMDLINE_LINUX_DEFAULT="vga=791"

save and run:

update-grub
reboot

---

### Post by alarme on 2011-03-12
Ooops, te contesté en inglés.

pues eso, edita /etc/default/grub

cambia la línea:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

por

GRUB_CMDLINE_LINUX_DEFAULT="vga=791"

guarda y ejecuta:

update-grub

reinicia

Salu2

---

