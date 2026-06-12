---
title: "Problema con Flash video en firefox"
date: 2009-07-02
forum: Software
---

### Post by mar_celo on 2009-07-02
Hola

Hay paginas que tienen videos en flash y no las puedo ver en ninguno de los navegadores, cuando veo las propiedades en la zona del video, veo que el programa que esta es el Swfdec 0.8.2, yo intente bajar el Adobe Flash y lo instale pero no lo veo en el firefox o el resto.

Alguien puede ayudarme

---

### Post by Pollito on 2009-08-01
tengo un problema yo ya instale el flash noseq de adobe que me pedia youtube para ver videos pero cuando pongo youtube en firefox se pone el computador lento y se queda pegado el video y solo se escucha
¿Que hago en ese caso?

---

### Post by Tclarkie on 2009-08-01
[LEFT]intenta instalar a través de un flash. deb enlace aquí 
 aquí es el doble clic. deb 
 [http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb)[/LEFT]

---

### Post by staar on 2009-08-01
porqué rapidshare? no bajes eso...

el plugin de flash para linux es malo, el bajo rendimiento es normal, lamentablemente adobe no se esfuerza mucho al hacerlo...

saludos

---

### Post by Tclarkie on 2009-08-01
[LEFT]esto podría ayudar a 
 aquí es el doble clic. deb (arquitectura podría estar equivocado)

---

### Post by Pollito on 2009-08-01
pero si ya tengo instalado el flash porsiacaso. cuando no lo tenia me salia un mensaje en youtube de que tenia que bajar el adobe flash pero depues de instalarlo abri youtube y funcionaba pero el video se quedaba pegado y solo se escuchaba.

---

### Post by staar on 2009-08-01
antes de instalar nada desde rapidshare, usá los respositorios...

el problema es que primero tenés que desinstalar swfdec, antes de instalar el de adobe, hacelo, y después reinstalá el de adobe...

saludos

---

### Post by guillermolisi on 2009-08-01
> **Tclarkie said:**
> [LEFT]intenta instalar a través de un flash. deb enlace aquí 
 aquí es el doble clic. deb 


Existiendo sitios confiables de Flash, por que usar Rapidshare ?

Inclusive, si el que esta en los repositorios no funciona/es obsoleto/otras razones, se puede recurrir al sitio oficial de Adobe para bajarlo.

Tclarkie, sugeriste Rapidshare por alguna cuestion en particular ?

---

### Post by jpoeta on 2009-08-02
Simplemente ve a Synaptic marca para desinstalar el SWFdec 
luego de eso Instala nuevamente el pluging oficial de Flash
De [Adobe ]("http://get.adobe.com/es/flashplayer/") Has click al enlace 
Y luego eliges Ubuntu Linux 
Asi de facil luego todo estara solucionado, yo tambien odié el SWFdec y lo desinstale inmediatamente.
Saludos 
Jpoeta:)

---

### Post by Hei Ku on 2009-08-02
Como regla general, aconsejamos a todos los usuarios que solo instalen software desde los repositorios oficiales. Justamente una de las ventajas de Ubuntu es que no hace falta andar buscando shareware y cracks por ahí. 

Por lo tanto, si el software está disponible, por favor pongan el link al repositorio oficial original. Enseñemos a hacer las cosas de manera segura con el ejemplo.

---

### Post by Tclarkie on 2009-08-03
esto funciona así montones [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

### Post by guillermolisi on 2009-08-03
> **Tclarkie said:**
> esto funciona así montones [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)
Thanks dude ....

En ese mismo thread hay mas de una referencia a sitios conocidos y otras a un blog cuya validez para bajar algo que no hace su autor lo pone en cierto grado de duda (once again).

**Validos/confiables**:

First you need to download the .deb package from [URL="http://www.adobe.com/shockwave/download/alternates/"]here
[/URL]sudo dpkg -i install_flash_player_10_linux.deb

sudo apt-get install adobe-flashplugin

**No confiables**:

Cualquier otro sitio que no sean los repositorios de Ubuntu y que no sean propiedad de quienes desarrollan el software/paquete/proyecto (generalmente alojados en Launchpad, GIT, etc.).

**Tclarkie**: Por favor, no recomiendes sitios no conocidos para bajar software. Hay personas que son asistidas en el foro que no tienen la suficiente experiencia como para saber de donde es confiable bajar software y de donde no.
(Please, do not recommend unknown sites for software downloading. There are people here with no experience to know which site is reliable and which is not for software downloading).

---

### Post by EnriqueK on 2009-08-03
Lo que hice fue instalar el paquete **ubuntu-restricted-extras**, recuerdo que durante el proceso de instalación el equipo se conectaba con el sitio de Adobe para descargar flash y esta descarga lo instalaba  directamente , o sea no era un paquete .deb , algo similar ocurre con las fuentes msttcorefonts.

---

### Post by guillermolisi on 2009-08-03
> **EnriqueK said:**
> Lo que hice fue instalar el paquete **ubuntu-restricted-extras**, recuerdo que durante el proceso de instalación el equipo se conectaba con el sitio de Adobe para descargar flash y esta descarga lo instalaba  directamente , o sea no era un paquete .deb , algo similar ocurre con las fuentes msttcorefonts.
En realidad usaste un paquete preparado por Canonical (**ubuntu-restricted-extras)**, bajado e instalado por apt-get**, **que hace lo que describis, con lo cual esta totalmente controlado y es confiable.

---

