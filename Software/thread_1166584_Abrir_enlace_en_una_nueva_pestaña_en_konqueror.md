---
title: "Abrir enlace en una nueva pestaña en konqueror"
date: 2009-05-21
forum: Software
---

### Post by guisheca on 2009-05-21
Que tal ubunteros, es algo tonta mi consulta pero no he encontrado otra alternativa que no sea preguntar acá.
Lo que quiero es simple: poder abrir los enlaces en una nueva pestaña de konqueror al hacer click con el boton del medio del mouse, tal como se hace en firefox. Estoy usando konqueror 4.2.2 en kde 4.2.3 (no se porque esa diferencia de versiones), en kubuntu 9.04.
Espero puedan ayudarme, recuerdo que alguna ves en versiones anteriores pude encontrar esto, pero ahora ya no :(.
Espero puedan ayudarme, saludos.

---

### Post by Hei Ku on 2009-05-21
Te fijaste en Configurar Konqueror -> Navegacion Web -> Comportamiento del raton -> La pulsacion del boton central del raton abre la URL seleccionada?

---

### Post by guillermolisi on 2009-05-21
Boton derecho sobre el link, ahi seleccionas "Open in new tab".

La otra es tildar la primera opcion tal como muestro en el screenshot, asi cuando haces click con el boton medio abre en una nueva solapa.

---

### Post by Hei Ku on 2009-05-21
No, no. El truco es con un solo click. ;)

---

### Post by guisheca on 2009-05-21
Naranja che. En cuanto a lo que me dijo Hei Ku, no hay tal opción (comportamiento del raton) en esa ruta. guillermolisi, ya tenía tildada esa opción :(.
Igual voy a seguir buscando, lo que pasa que no quería dejar de postear por las dudas que alguien lo sepa.

---

### Post by Hei Ku on 2009-05-21
Esto es lo que yo veo en mi Konqueror 4.2.2 KDE 4.2.3

---

### Post by guisheca on 2009-05-21
Vos sabes que ya tenía activado eso mismo y le doy al boton del medio y no me da artículo che. Tiene que ser algo del mouse, voy a ver en la config del mismo.

---

### Post by guillermolisi on 2009-05-21
> **guisheca said:**
> Vos sabes que ya tenía activado eso mismo y le doy al boton del medio y no me da artículo che. Tiene que ser algo del mouse, voy a ver en la config del mismo.
Si, tiene que ser algo del mouse porque lo volvi a probar y en mi caso funciona perfecto.

Tengo un Genius NetScroll Eye (dos botones + ruedita/tercer boton) PS/2.

---

### Post by guisheca on 2009-05-21
Tendré que modificar algo en el xorg.conf?? este es mi xorg actual:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

En cuanto al mouse no es nada del otro mundo, es un genius comun y corriente con tres botones obviamente en el cual el del medio tambien es ruedita. No tiene nada de raro digamos como para que no me lo tome correctamente, pero quizás haya que editar el xorg.conf.

---

### Post by guisheca on 2009-05-21
Veran me paso algo muy extraño, resulta que tenía abierto el nautilus en kde4 (si ya se que nada que ver, pero dolphin como root mediante kdesu no lo podia abrir y nautilus si). Cambié de mouse, puse uno usb que es de la notebook de mi hermana y para ver que pasaba reinicié las X. Sorprendentemente me inició (sin que hiciera nada) una sesión en pseudo gnome (nunca instale el escritorio, solo nautilus y synaptic), en la cual pude abrir konqueror y todo funcionaba a las mil maravillas, es decir funcionaba el raton como quiero. Intente volver a kde, pero no pude así que comencé a desinstalar las cosas de gnome que, evidentemente, estaban en conflicto (nautilus y demás). Una ves en el querido kde el mouse volvió a la situación anterior en la que no me funcionaba el boton del medio para lo que quiero, y estoy con el otro mouse.
En fin, supongo que es algo de KDE que no tengo instalado quizás. A alquien se le ocurre algún paquete que me este haciendo falta?
Saludos y gracias por la ayuda.

---

### Post by Hei Ku on 2009-05-22
Mira, lo mas facil es que le des sudo aptitude reinstall kubuntu-desktop

---

### Post by guisheca on 2009-05-22
Que tal muchachos, al final pude solucionar el tema, fue un poco drástica la solución pero funcionó: Borré todas las configuraciones en mi home. Es decir, todas las carpetas que tenían un puntito adelante y hacían referencia a kde o gnome.
Con eso salio todo andando de 10.
Saludos y gracias por el aguante.

PD: No se como poner [solucionado] :(

---

### Post by guillermolisi on 2009-05-22
> **guisheca said:**
> Que tal muchachos, al final pude solucionar el tema, fue un poco drástica la solución pero funcionó: Borré todas las configuraciones en mi home. Es decir, todas las carpetas que tenían un puntito adelante y hacían referencia a kde o gnome.
Con eso salio todo andando de 10.
Saludos y gracias por el aguante.

PD: No se como poner [solucionado] :(
Edita tu primer mensaje y en el campo llamado Title le agregas el tag/prefijo [Solucionado]

---

