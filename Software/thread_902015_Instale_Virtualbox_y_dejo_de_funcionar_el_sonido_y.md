---
title: "Instale Virtualbox y dejo de funcionar el sonido y la red"
date: 2008-08-26
forum: Software
---

### Post by motochucho on 2008-08-26
Bueno, este es mi primer post, a ver que tal...

Todo funcionaba de maravilla con mi UBUNTU Hardy, y necesitaba hacer unos planos y el programa DIA no me era tan util en ese momento, asi es que necesitaba urgente mente MS Visio, para tal razon intente instalarlo con WINE y no me funciono. 

Instale virtualbox y lo quise instalar desde el synaptic y me dio un error, lo desinstale, hasta que lo termine instalando con "agregar o eliminar programas" y funciono bien, cuando estaba configurando virtualbox (dispuesto a instalar xp) me puse a configurar las opciones de audio, y de la red dentro de virtualbox.

Para mi sorpresa cuando quise instalar XP no me funciono y decidi por desintalar Virtualbox y reiniciar mi maquina, y al cargar y inmediatamente observe una "X" sobre mi control de Sonido en la barra, al igual que en mi indicador de Wireless.

Al parecer como que se desconfiguro mi ubuntu y no me reconoce ni tarjeta de audio, ni tarjeta wireless.

El mensaje que me da cuando doy click sobre el control de volumen es:

"El control de volumen no encontró ningùn elemento y/o dispositivo que controlar. Esto significa que no tiene los complementos correctos de GStreamer instalados o que no tiene un tarjeta de sonido configurada"

y cuando doy clik sobre configuracion de red, solo me aparece:
"configuración cableada, y Configuracion punto a punto"
no me aparece la opcion de Inalambrico.

Habria alguna manera de regresar a un estado anterior????

o Como puedo Solucionarlo??? ayuda por favor...

Mi computadora es una DELL XPS M1210

---

### Post by motochucho on 2008-08-27
Ayuda por favor... Realmente no se que hacer??? y ya no se me ocurre nada!

---

### Post by faktorqm on 2008-08-28
> **motochucho said:**
> Todo funcionaba de maravilla con mi UBUNTU Hardy, y necesitaba hacer unos planos y el programa DIA no me era tan util en ese momento, asi es que necesitaba urgente mente MS Visio, para tal razon intente instalarlo con WINE y no me funciono.

Primero deberias haberte fijado si Visio esta soportado por Wine, principalmente para no perder tanto tiempo. lista de appz soportadas por wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)

> **motochucho said:**
> Instale virtualbox y lo quise instalar desde el synaptic y me dio un error,

Que tipo de error? error de dependencias? problemas con internet? .deb's corrupto? no alcanza con "me dio un error y lo cerre".....

> **motochucho said:**
> lo desinstale,

Como hiciste? no era que no lo instalaste por que te tiro un error? 

> **motochucho said:**
> hasta que lo termine instalando con "agregar o eliminar programas" y funciono bien, cuando estaba configurando virtualbox (dispuesto a instalar xp) me puse a configurar las opciones de audio, y de la red dentro de virtualbox.

Para mi sorpresa cuando quise instalar XP no me funciono

De vuelta, que error tira? error de Vbox o del instalador de xp?

> **motochucho said:**
> y decidi por desintalar Virtualbox y reiniciar mi maquina, y al cargar y inmediatamente observe una "X" sobre mi control de Sonido en la barra, al igual que en mi indicador de Wireless.

Al parecer como que se desconfiguro mi ubuntu y no me reconoce ni tarjeta de audio, ni tarjeta wireless.

El mensaje que me da cuando doy click sobre el control de volumen es:

"El control de volumen no encontró ningùn elemento y/o dispositivo que controlar. Esto significa que no tiene los complementos correctos de GStreamer instalados o que no tiene un tarjeta de sonido configurada"


fijate en una consola de escribir "alsa-mixer" y ahi te muestra que dispositivos tenes, sino, aunque no creo que sea la solucion podes escribir "sudo apt-get install gstreamer*" (sin comillas) y te instala todos los paquetes gstreamer.

> **motochucho said:**
> y cuando doy clik sobre configuracion de red, solo me aparece:
"configuración cableada, y Configuracion punto a punto"
no me aparece la opcion de Inalambrico.

Habria alguna manera de regresar a un estado anterior????

o Como puedo Solucionarlo??? ayuda por favor...

Mi computadora es una DELL XPS M1210

Deberia aparecerte "conexión cableada" y "conexión punto a punto". Más allá de eso, el network manager (a veces) puede fallar. Poné ifconfig y te lista todos los dispositivos de red que tengas, deberias tener uno que se llama wlan.

Yo lo que creo es que se te instalo una nueva version de kernel con una actualizacion involuntaria y te rompio 2 drivers. Para bootear con "el viejo" podes desde el grub elegir una version anterior de kernel para arrancar y asi seguro te toma todo de vuelta. Salu2!!

---

