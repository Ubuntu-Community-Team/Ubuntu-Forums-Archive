---
title: "Protocolo asociado?"
date: 2011-08-11
forum: Software
---

### Post by tutumi on 2011-08-11
Estoy intentando instalar adobe flash player y me sale una ventanita que dice...el protocolo no esta asociado a ningun programa...por favor me podrian guiar para resolver esto? No tengo experiencia...o sea que les agradeceré sean básicos/ hiperclaros/ en lo que tendria que hacer!!! Gracias!!!!!:confused:

---

### Post by granjero on 2011-08-11
tutumi, contanos antes cómo es que estás instalando? desde los repositorios? 

yo cuando quiero flash lo que hago es instalar el paquete "ubuntu-restricted-extras" tanto desde consola como desde synaptic o del centro de soft. Eso te instala otras cosas también pero son útiles.

salud!

---

### Post by tutumi on 2011-08-11
Gracias por tu respuesta. 
Lo que intenté hacer fue ir directamente a la pagina de adobe, [http://get.adobe.com/es/flashplayer/](http://get.adobe.com/es/flashplayer/) y ahí me ofrece varias versiones para linux, una de ellas para ubuntu APT 10.04.
Intenté bajarla y me dice lo de ...no hay protocolos asociados...
Intenté bajar una versión distinta, la bajó pero no pude instalarla.
Creo que lo primero que necesitaría saber es cuál de las versiones es compatible con mi sistema.
Tengo Ubuntu 9.04 Jaunty. Nucleo Linux 2.6 28-19 Gnome 2.26.1

Las posibilidades que encontré son:
[Download plug-in for Linux 32-bit]("http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_32_080811.tar.gz") (TAR.GZ, 6.4 MB)
[Download plug-in for Linux 64-bit]("http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_64_080811.tar.gz") (TAR.GZ 6.7 MB)

Aquí todos son muy expertos...y yo no sé cuál es la diferencia entre 32 y 64 bits, o dónde ubicar esa info en mi compu. 
Si hay una forma más sencilla...muy agradecida!!!

---

### Post by granjero on 2011-08-11
yo no sé como hacer para instalar sólo flash.

si no te molesta instalar complementos para escuchar mp3, ver mpeg, y tener las fuentes M$, como te dije antes instalate el paquete "ubuntu-restricted-extras" y flash te va a andar joya.

salud!

---

### Post by Martinius on 2011-08-11
Hola tutumi, como granjero te dijo lo más simple es instalar flash desde uno de los gestores de paquetes de Ubuntu, sea el centro de software o synaptic. Así lo hago yo.
El problema con la versión de Ubuntu que estás usando, 9.04, es que ya no tiene soporte y por lo tanto no tiene actualizaciones ni podés instalar programas desde los repositorios. Por lo tanto te recomendaría que instales si es posible la versión 10.04 (que tiene actualizaciones por tres años) o la 11.04.

---

### Post by granjero on 2011-08-11
creo que lo que no te brindan las versiones que no tienen más soporte es eso. más soporte. 

la 9.04 después de instalarla; se actualiza a lo último que tuvo la 9.04 y listo.

andá a Sistema > Administración > Gestor de paquetes Synaptic

te pedirá la clave

buscá el paquete ubuntu-restricted-extras y leé qué es lo que instala y si te parece bien dale ok.

salud!

---

### Post by tutumi on 2011-08-12
Gracias voy a intentarlo!

---

### Post by tutumi on 2011-08-12
Algo no anduvo bien....hice exactamente eso y aparece lo siguiente:

E: No se pueden corregir los paquetes que faltan

W: Falló al obtener [http://security.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-3+lenny1build0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-3+lenny1build0.9.04.1_i386.deb)
  404 Not Found

Esto les permite darme alguna pista???? Desde ya muchísimas gracias por su ayuda!!!!

---

### Post by granjero on 2011-08-12
tenés tu sistema actualizado? 
que servidor estás usando?

Sistema > Administración > Orígenes de Software

te pedirá ti clave

elegí servidor principal. recargá y volvé a intentar. 

debería arrancar.

salud!

---

### Post by tutumi on 2011-08-12
Granjero gracias por tu paciencia y buena onda, pero por ahora me doy por vencida.
El servidor está como principal,
y actualizado,
pero apagué y reinicié, y ahora no aparece ubuntu restricted extras en el gestor de paquetes.
SAludos!

---

### Post by gmunioz on 2011-08-13
Hola tutumi:
*"....pero por ahora me doy por vencida...."*
¿cómo que vencida?
Descarga este archivo:
[http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_32_080811.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_32_080811.tar.gz)
Luego cargas Nautilus, navegas hasta la carpeta de descarga, abres el archivo pulsando dos veces sobre el archivo y extraes el archivo libflashplayer.so
Cierras Nautilus y en una terminal ejecutas
sudo su
nautilus
Para iniciar el navegador con permisos temporarios de administrador, navegas hasta el archivo extraido  libflashplayer.so. lo copias y lo pegas en 
/usr/lib/adobe-flashplugin/ 
y en 
/usr/lib/firefox/plugins/
Lo correcto seria hacer un enlace simbólico con la orden
sudo su
 ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so

---

