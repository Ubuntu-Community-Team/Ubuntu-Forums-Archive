---
title: "Demasiado uso de CPU."
date: 2008-12-20
forum: Software
---

### Post by morefeo on 2008-12-20
Buenas, hace dos días instale ubuntu 8.0.4 en mi ordenador(A.K.A. computadora/pc).

Deje que se actualizase lo necesario, instale el compiz fusion lo probe un rato e iba como la seda, podía incluso grabar video.

Luego intenté usar cierto grabador, beryl-vidcap, asi que me puse a instalar dicho programa. No me convencía lo que estaba haciendo así que le di puerta y usé:
```
apt-get remove --purge beryl
```

Desde entonces el solo hecho de usar el monitor del sistema para ver la cantidad de cpu usada hace que se ponga sobre 90%, si abro dos "emesene" a la vez, y los coloco en distintos escritorios, me tarda segundos en pasar de un escritorio a otro, además de notarlo más lento.

No se a que se debe este repentino y bestial incremento de uso de la cpu, espero alguien sepa por qué es.

Los datos de mi equipo son:
Procesador: amd athlon xp 3200 a 2.1ghz
Memoria: 512 mb.
Gráfica: ATI Sapphire Radeon 9200 pro family, 128 mb de memoria.

Gracias por la ayuda de antemano.

---

### Post by c4d0rn4 on 2008-12-20
no entendí el tema de quien se pone a usar la cpu a todo dar.

gnome-system-monitor algunas veces el solo pide bastante cpu. Si te querés fijar sin meterle un proceso extra en la terminal ejecuta
```
top
``` fijate quien es el que te causa problemas.

---

### Post by morefeo on 2008-12-20
Parece que he dado con el causante, el xorg.
```
 6048 root      20   0  336m  53m 9084 R 75.9 10.7  13:58.19 Xorg               
 6956 slake     20   0  123m  66m  16m R 14.0 13.2   1:34.35 python 
```

El python supongo que será por que estaba usando dos "emesene"(uno tiene 1000 contactos).

---

### Post by KrossX on 2008-12-20
Prueba desactivando Compiz y reconfigurando X.

---

### Post by morefeo on 2008-12-20
Suelo tenerlo desactivado, y la verdad no sé como configurar X...¿Puede que sea por la actualización de Ubuntu a 8.1?

---

### Post by KrossX on 2008-12-20
Si puedes acceder al X, entonces sólo tienes que editar el archivo:

/etc/X11/xorg.conf

No sé cual pueda ser el problema. Quizá volvió al driver por defecto en lugar del propietario para tu ATI.

---

### Post by morefeo on 2008-12-21
Éste es el archivo en cuestión:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

¿Se ve algo..mal?

---

### Post by KrossX on 2008-12-21
> Section "Device"
........Identifier	"Configured Video Device"
........[COLOR="Red"]Driver <= Desapareció?[/COLOR]
EndSection

[COLOR="Navy"]Eso es lo único raro que veo ahí. Usa la configuración del X para seleccionar un driver apropiado.
O si tienes drivers propietarios, prueba volver a activarlo.
Sistema => Administración => Drivers Hardware (del inglés)[/COLOR]

---

### Post by morefeo on 2008-12-21
No tengo el driver propietario de la ATI, en su lugar uso el de código abierto del paquete xserver-xorg-video-ati, por lo que en dicha ventana no me aparece ningún driver,¿Debería instalar el propietario?.

---

### Post by KrossX on 2008-12-21
[COLOR="Navy"]Pues, a mi parecer, los drivers propietarios brindan mejor performance (nVIDIA). Aunque algunos quizá sean problemáticos. (Intel IGPs)

De todas formas, incluso si no es propietario debería estar explícito en el .conf. Es probable que esté cargando uno por defecto como vga o svga en lugar del más apropiado para tu Video.

Prueba reconfigurar X y selecciona tu driver de Video, o hazlo manualmente si sabes que driver debería estar usando[/COLOR]

# Xorg -configure
[COLOR="Navy"]Debería servir.[/COLOR]

---

### Post by morefeo on 2008-12-22
¿Cómo se reconfigura X? Siento la pregunta pero soy novato en Ubuntu.

Añado: El python, cuando envío archivos por "emesene" utiliza entorno un 70% de CPU. ¿Alguien sabe la causa?

---

### Post by anarko on 2008-12-23
El X se configura con ```
sudo dpkg-reconfigure xserver-xorg
``` o algo muuuuy parecido.
A mi el emesene me hace lo mismo cuando transfiere archivos se abusa del uso del micro.
Tambien me pasa lo del X pero no es problema de conf. yo todabia no pude encontrar cual es el problema, pero despues de un cierto tiempo de usar la PC ( algunas muchas horas ) se pone a usar el 100% de uno de los cores.
Solucion, sudo reboot.

---

