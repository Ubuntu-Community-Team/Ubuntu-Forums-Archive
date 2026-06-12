---
title: "[Problema] FretsOnFire y gfxboot en Intrepid Ibex"
date: 2008-11-02
forum: Software
---

### Post by emancu on 2008-11-02
Si bien es mi primer post que realizo, hace tiempo que leo el foro ya que me soluciono muchos problemas sin siquiera escribir porque ya habian sido planteados.

Sin embargo, estuve buscando sobre mi problema y no encuentro y paso a detallar.

Mi PC es un AMD Phenom 9550 x4, mother Asus a3m, y geforce 8500.

Tenia instalado Ubuntu 8.04 64bits y andaba muy bien, la verdad estaba conforme, tenia unos problemitas con el audio y FoF en simultaneo que se solicionaban y se volvian a romper pero nunca fue un gran problema. 
Andaba todo.. desde el gfxboot hasta youtube + amarok + kaffeine al mismo tiempo y sin problemas (si uso ubuntu con aplicaciones de KDE).

El problema surge cunado salio la tan esperada 8.10, inmediatamente actualice a la nueva version y para mi sorpresa seguia andando todo igual de bien, el gfxboot, video.. hasta se soluciono por completo el problema que tenia con el audio!, contento con esto decidi jugar al FretsOnFire (adicto a este juego) como de costumbre y aca me encuentro con el primer problema, anda mal!
 
El problema parece ser de video porque lo que hace es como si se adelantaran las notas tras un "semicorte" de imagen.. no se si se entiende.. es como si se trabara el juego y continuara entonces los graficos no son fluidos, algo esencial para el juego.

Probe cambiando los drivers de la nvidia (instalados con el envyng), 177 y 173 los probe y siempre el mismo resultado.
Sacrifique el compiz, e intente denuevo y nada cambio.

Baje la version de Ubuntu 8.10 32 y 64 bits e instale la de 32bits porque en 32bits recordaba una mejor experiencia y ademas unos programitas en 64 no estaban.

Termina la instalacion DESDE CERO y todo perfecto.. instalo los drivers configuro el sistema y checkeo que ande todo bien, llega le momento del FoF y otra vez lo mismo!!! la verdad no tengo ganas de volver a formatear e instalar todo, pero quiero resolver lo del FoF.

Y para colmo.. no puedo instalar el gfxboot en intrepid, cuando intento instalar el grub me dice que no puede leer el archivo "/boot/grub/stage1" que esta pero no se puede abrir.

Este ultimo error es lo de menos.

La verdad estoy desilucionado con Intrepid Ibex, me dio una felicidad por lo del sonido pero hasta me parece mas lento! el Firefox tarda bastante en arrancar (sera porque es 32 bits y venia acostrumbrado a 64?)

Gracias a todos por los que llegaron al final de este largo post ^^ espero que me puedan ayudar a solucionar lo del FoF.

---

### Post by elpotrito on 2008-11-03
Me sumo al pedido de instalar gfxboot desde el 8.10. A mi me lo sobreescribio la instalacion de cero del 8.10 por el grub comun. Y cuando quiero instalar el gfxboot me dice lo mismo que dice el compañero emancu

---

### Post by faktorqm on 2008-11-04
Hola, el gfxboot les recomendaria que lo dejaran de lado hasta que se sepa que anda en 8.10. Con respecto al juego, deberias fijarte primero si tenes aceleracion 3d y eso lo averiguas con el comando

```
glxinfo | grep direct
```

Si dice "direct rendering: yes" podes leer aca que te dice como buscar errores en el juego, [http://fretsonfire.wikidot.com/error-messages](http://fretsonfire.wikidot.com/error-messages), y si sigue con el mismo problema, deberias pensar en como tocar el xorg.conf para que funcione (el driver de nvidia tiene muchos tweaks para solucionar estos inconvenientes). Salu2!!!

---

### Post by emancu on 2008-11-04
> **faktorqm said:**
> Hola, el gfxboot les recomendaria que lo dejaran de lado hasta que se sepa que anda en 8.10. Con respecto al juego, deberias fijarte primero si tenes aceleracion 3d y eso lo averiguas con el comando

```
glxinfo | grep direct
```

Si dice "direct rendering: yes" podes leer aca que te dice como buscar errores en el juego, [http://fretsonfire.wikidot.com/error-messages](http://fretsonfire.wikidot.com/error-messages), y si sigue con el mismo problema, deberias pensar en como tocar el xorg.conf para que funcione (el driver de nvidia tiene muchos tweaks para solucionar estos inconvenientes). Salu2!!!

Afortunadamente me dice "direct rendering: yes" pero desafortunadamente no tengo un error en el juego, sino que anda lento nomas, como que el juego "tira".

Alguien me ayuda con el Xorg.conf?

Mi archivo /etc/X11/xorg.conf es el siguiente
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
```

Y la otra info que encontre en /xorg.conf.new se las pongo aca..
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "glx"
	Load  "xtrap"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 8500 GT"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

