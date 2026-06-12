---
title: "configuración sonido rec + ustream"
date: 2011-09-21
forum: Software
---

### Post by granjero on 2011-09-21
hola, ando tratando de hacer andar una máquina con ubuntu 10.04 que tiene chip VIA 82xx. Me sucede lo siguiente:

Todo parece funcionar correctamente. Graba con el grabador de sonidos y con Audacity lo que entra por el line-in correctamente. Pero cuando quiero transmitir por Ustream (cosa que hago con otras 5 pc ccon ubuntu 10.04) no transmite. Pero si cierro audacity o el grabador de sonidos si transmite.

Pero si está transmitiendo y trato de grabar no graba. 

Alguno sabe por donde encarar el tema? leyendo le agregué a /etc/modules la linea via82xx (para que cargue el modulo al inicio) pro sigue igual.

También traté de ponerle una placa pci 5.1 (génerica) no agrego los datos porque no estoy con la pc ahora, y ni siquiera la toma en la configuración de audio. Sin embargo lspci la ve.

Saludos!

---

### Post by granjero on 2011-09-23
al final era un problema del flash player.

desinstalé flash-plugin-installer desde synaptic y luego marqué allí mismo que se instale una versión vieja.

y salió andando.

salud!

---

### Post by granjero on 2011-09-27
agrego otra forma en la que solucioné el mismo problema que con la solución anterior no anduvo.

[http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html) en esta página hay versiones viejas de flash. con la versión 10.2.152 me funcionó

desisntalé por completo flash-plugin-installer y flash-nonfree desde synaptic.

descomprimí el archivo flashplayer.so y lo copié a /usr/lib/mozilla/plugins y listo.

---

