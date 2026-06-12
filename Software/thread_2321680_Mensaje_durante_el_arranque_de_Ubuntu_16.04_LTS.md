---
title: "Mensaje durante el arranque de Ubuntu 16.04 LTS"
date: 2016-04-23
forum: Software
---

### Post by drazhe on 2016-04-23
Hola, acabo de hacer una instalación limpia de **Ubuntu 16.04 LTS x64 Final** y todo parece funcionar bien, pero durante el arranque donde debería aparecer el logo de Ubuntu con los puntitos cambiando de color, **da varios saltos la imagen y aparece el siguiente mensaje....**

[IMG]http://i63.tinypic.com/166nhw3.jpg[/IMG]

Luego después de unos saltos más finalmente carga el escritorio y el sistema funciona con normalidad...


Quisiera saber a que se debe y como solucionarlo.... ya instale los drivers propietarios de NVIDIA y aún da los saltos de imagen...


¡Desde ya muchas gracias por su atención!

---

### Post by Cajuma on 2016-07-23
[COLOR=#404040][FONT=&quot]Proba lo siguiente:[/FONT][/COLOR]

[LIST]
[*]vía terminal colocamos: **sudo gedit /etc/default/grub**
[*]Buscamos la línea **#GRUB_GFXMODE=640×480** y debajo de esta colocamos:[FONT=inherit]&#8211; **GRUB_GFXMODE=1366x768x24** (esto dependerá de cuál es la resolución de tu pantalla, en mi caso, la resolución es 1366×768)
&#8211; **GRUB_GFXPAYLOAD_LINUX=keep**
[[IMG]https://libuntu.files.wordpress.com/2015/05/cambios-splash-screen-ubuntu.png?w=700[/IMG]]("https://libuntu.files.wordpress.com/2015/05/cambios-splash-screen-ubuntu.png")[/FONT]

[*]Guardamos los cambios abrimos la terminal y colocamos:[FONT=inherit]&#8211; **echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash**
&#8211; **sudo update-initramfs -u**
&#8211; **sudo update-grub2**[/FONT]
[/LIST]
[COLOR=#404040][FONT=&quot]Con estos cambios debería funcionar correctamente el Splash Screen tanto al finalizar sesión como al iniciar sesión, obviamente luego de esto, reiniciamos!
P/D: Es posible que luego de alguna actualización del kernel, se tenga que volver a realizar nuevamente el paso del framebuffer.
Fuente= LIBUNTU.
Saludos.[/FONT][/COLOR]

---

