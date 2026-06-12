---
title: "Problema de instalacion ubuntu 10.04"
date: 2011-08-15
forum: Software
---

### Post by figoberto on 2011-08-15
[FONT="Tahoma"][COLOR="Navy"]Hola a todos, 

Tengo una VAIO VPCCW21FX con WIN 7 e descargado UBUNTU 10.04 y lo e instalado dentro de win7 pero cuando me pide reiniciar y que escoja el Sistema con ubuntu me deja la pantalla negra y no hace nada..

que pudo hacer ?

saludos
[/COLOR][/FONT]

---

### Post by marcelo_bur on 2011-08-15
Hola.
Te comento que anteriormente intenté correr Ubuntu 10.04 dentro de XP y, si bien a veces funcionaba, siempre en algún momento fallaba y tenía que reinstalar, y a veces requería de varios intentos antes de lograr que vuelva a funcionar. Así que finalmente hice lo más lógico y, según todos los que saben, lo más recomendable, instalar Ubuntu en una partición del disco, lo cual lo hace el mismo programa de instalación. Desde entonces no he tenido más problemas y ya casi no tengo necesidad de usar XP. 
De todas formas seguramente alguno de los miembros de este foro, queen su mayoría saben mucho más que yo, te dará mayores precisiones.
Saludos

---

### Post by figoberto on 2011-08-16
Gracias marcelo_bur pero me sigue dejando la pantalla negra...  lo trate de instalar en una partición a la hora de instalarlo me salio la pantalla morada de la instalación de ubuntu unos segundos y después me sale la pantalla en negro y de pierde vídeo.. 
 
yo creo que es problema de incompatibilidad pero bueno..

si alguien me pudiera dar una solución se los agradecería

saludos.

---

### Post by gmunioz on 2011-08-16
Sugerencia:
Dado que la PC tiene una placa Nvidia 310M, seguramente es problema de compatibilidad de video.
1- Puedes intentar instalar con el live-cd que tienes, eligiendo safe mode al inicio del sistema.
2- Instala con el alternate-cd, tiene un instalador en modo semigráfico que es posible no tenga problemas con el video.
3- Es conveniente instalar en particiones separadas, para ello deberás seguir cualquier tutorial, que los hay en demasía como para repetirlos.
4- antes de instalar, busca en la red acerca de tu tarjeta de video y los problemas que puede presentar, por ejemplo alguien que dice haber solucionado los problemas lo hizo mediante este procedimiento (en inglés)
=========================================================================
1) Remove all nvidia packages ( you can do this through synaptic)
2) download the files and install this [https://launchpad.net/ubuntu/+source...+build/1973339](https://launchpad.net/ubuntu/+source...+build/1973339).

(for this step I found a deb on a related forum: [http://dl.dropbox.com/u/737114/vpcs1...ntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs1...ntu3_amd64.deb) and [http://dl.dropbox.com/u/737114/vpcs1...ntu1_amd64.deb](http://dl.dropbox.com/u/737114/vpcs1...ntu1_amd64.deb)

Here is the forum link: [http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup](http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup)

3) This is where I tried something different, I read somewhere that you MUST use linux kernel 2.6.36, go to [http://kernel.ubuntu.com/~kernel-ppa...6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa...6.36-maverick/) (thanks to Artem161 from [http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup](http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup)). Download the appropriate architecture files. I downloaded headers, image and headers-amd64
4) Use the custom EDID option in /etc/X11/xorg.conf
*my edid file is located in /proc/acpi/video... yours might be different.
Option "ConnectedMonitor" "DPF-0"
Option "CustomEDID" "DPF-0: /proc/acpi/video/IGPU/LCD0/EDID"
Option "RegistryDwords" "EnableBrightnessControl=1" # For brightness control

This is also from: [http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup](http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup)

before I could add this I had to generate the xorg.conf file with: sudo nvidia-xconfig then opened it with: sudo gedit /etc/X11/xorg.conf
adding the lines under section device. The brighness controls aren't fixed for me but I don't really care, its further discussed in the forums.

If the custom path for the edid does not here is a link to another thread discussing another way to obtain with other cards.

[http://www.nvnews.net/vbulletin/show...3&postcount=22](http://www.nvnews.net/vbulletin/show...3&postcount=22)

5)
sudo update-alternatives --config gl_conf (I picked manual)
sudo ldconfig
sudo nvidia-xconfig
sudo reboot
=========================================================================

---

