---
title: "recuperar entorno grafico en KK"
date: 2010-01-24
forum: Software
---

### Post by krackmu on 2010-01-24
Hola, me mandé una embarradita y no tengo entorno grafico (mas encima un tiempo atrás desinstalé la consola de recuperacion).
Lo que hice, fue que intente instalar un controlador ATI que supuestamente funcionaba con mi tarjeta de video que esta obsoleta, y al reiniciar, quedo la grande!... no inicia el entorno grafico. Sale grub y el logo de ubuntu cuando caraga (el primer logo), despues de eso, solo una pantalla negra me acompaña... :(

como les dije antes, no tengo consola, asi que para mi, creo que la unica opcion es utilizando el live cd de ubuntu, pero no se que hacer.

Me hechan una manito.

PD. harto tiempo sin escribir acá, el medio cambio del foro.
PD2. mi tarjeta de video es una ATI RADEON X1650 PRO.

---

### Post by serbesa on 2010-01-25
Para arrancar KDE:startx kde
 Para arrancar Gnome: startx gnome


yo intale ubuntu mini, y despues instale el entorno grafico así, quizas te sirva, si es que no tienes instalado el entorno grafico:

[LIST]
[*]*sudo apt-get install xubuntu-desktop (si deseas instalar Xubuntu)*
[*]*sudo apt-get install ubuntu-desktop (si deseas instalar Ubuntu)*
[*]*sudo apt-get install kubuntu-desktop (si deseas instalar Kubuntu)*
[/LIST]

para instalar gnome y gdm tambien puedes (kdm y gdm son los gestores de entrada)

sudo aptitude install gdm gnome-core
 

 para kde 

sudo apt-get install kdm kde-core

---

### Post by serbesa on 2010-01-25
sorry no leí que no tenías consola....

---

### Post by moreback on 2010-01-25
Debiera tener disponibles las consolas de texto, accesibles con CTRL + ALT + {F1, F2, F3, F4, F5, F6}

Saludos.

---

### Post by krackmu on 2010-01-25
> **moreback said:**
> Debiera tener disponibles las consolas de texto, accesibles con CTRL + ALT + {F1, F2, F3, F4, F5, F6}

Saludos.

no, es que ni siquiera alcanzo a loguarme como usuario.

---

### Post by krackmu on 2010-01-25
no entiendes, lo que pasa es que instale unos controladores de videos que parece no eran compatibles. Entonces, no tengo ni se como arreglar la configuracion gráfica.

oigan, pude acceder a consola.

así:

```
en grub 2; presionar "e" al seleccionar S.O.
```

```
Ir a la linea del kernel y al final de la ruta se escribe: "single"
```

```
presionar ctrl+X
```
y arranca la consola de recuperacion.

ahora falta arreglar la parte grafica.

---

### Post by Carlos C on 2010-01-26
Edita tu archivo /etc/X11/xorg.conf. Ahí debieras tener seleccionado el driver de video. Si no me equivoco puedes dejarlo como vesa para que utilice el genérico. En caso de no tener ese archivo puedes, desde la consola de recuperación, crearlo con el comando:
```
Xorg -configure
```Con eso crearás el archivo /root/xorg.conf.new que debes copiar en /etc/X11/xorg.conf

Saludos.

---

### Post by krackmu on 2010-01-27
hice lo que me dijiste carlos c, pero no me funciona, lo edite y lo cambie a vesa el driver de video, pero al reiniciar queda igual, no se que pueda ser.

alguna idea?

Saludos.

---

### Post by Carlos C on 2010-01-27
Copia acá como lo pones en el xorg.conf.

Cuando dices que queda igual, ¿te refieres a que el archivo no cambia o a que a pesar de que el archivo se modifica no hay diferencia?

¿Generaste un archivo desde cero como te sugerí?

Saludos.

---

### Post by krackmu on 2010-01-27
Claro, lo genere porque no existía, y cambie el driver a vesa, al reiniciar, queda igual.

Ahi va mi xorg.conf

```
    Section "ServerLayout"
       Identifier     "X.org Configured"
       Screen      0  "Screen0" 0 0
       InputDevice    "Mouse0" "CorePointer"
       InputDevice    "Keyboard0" "CoreKeyboard"
    EndSection

    Section "Files"
       ModulePath   "/usr/lib/xorg/modules"
       FontPath     "/usr/share/fonts/X11/misc"
       FontPath     "/usr/share/fonts/X11/cyrillic"
       FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
       FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
       FontPath     "/usr/share/fonts/X11/Type1"
       FontPath     "/usr/share/fonts/X11/100dpi"
       FontPath     "/usr/share/fonts/X11/75dpi"
       FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
       FontPath     "built-ins"
    EndSection

    Section "Module"
       Load  "dri"
       Load  "glx"
       Load  "dbe"
       Load  "extmod"
       Load  "dri2"
       Load  "FGL.renamed.libdri"
       Load  "FGL.renamed.libglx"
       Load  "record"
    EndSection

    Section "InputDevice"
       Identifier  "Keyboard0"
       Driver      "kbd"
    EndSection

    Section "InputDevice"
       Identifier  "Mouse0"
       Driver      "mouse"
       Option       "Protocol" "auto"
       Option       "Device" "/dev/input/mice"
       Option       "ZAxisMapping" "4 5 6 7"
    EndSection

    Section "Monitor"
       #DisplaySize     410   260   # mm
       Identifier   "Monitor0"
       VendorName   "AOC"
       ModelName    "912Sw"
       HorizSync    30.0 - 83.0
       VertRefresh  55.0 - 75.0
       Option       "DPMS"
    EndSection

    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
            ### [arg]: arg optional
            #Option     "NoAccel"               # [<bool>]
            #Option     "SWcursor"              # [<bool>]
            #Option     "Dac6Bit"               # [<bool>]
            #Option     "Dac8Bit"               # [<bool>]
            #Option     "BusType"               # [<str>]
            #Option     "CPPIOMode"             # [<bool>]
            #Option     "CPusecTimeout"         # <i>
            #Option     "AGPMode"               # <i>
            #Option     "AGPFastWrite"          # [<bool>]
            #Option     "AGPSize"               # <i>
            #Option     "GARTSize"              # <i>
            #Option     "RingSize"              # <i>
            #Option     "BufferSize"            # <i>
            #Option     "EnableDepthMoves"      # [<bool>]
            #Option     "EnablePageFlip"        # [<bool>]
            #Option     "NoBackBuffer"          # [<bool>]
            #Option     "DMAForXv"              # [<bool>]
            #Option     "FBTexPercent"          # <i>
            #Option     "DepthBits"             # <i>
            #Option     "PCIAPERSize"           # <i>
            #Option     "AccelDFS"              # [<bool>]
            #Option     "IgnoreEDID"            # [<bool>]
            #Option     "DisplayPriority"       # [<str>]
            #Option     "PanelSize"             # [<str>]
            #Option     "ForceMinDotClock"      # <freq>
            #Option     "ColorTiling"           # [<bool>]
            #Option     "VideoKey"              # <i>
            #Option     "RageTheatreCrystal"    # <i>
            #Option     "RageTheatreTunerPort"    # <i>
            #Option     "RageTheatreCompositePort"    # <i>
            #Option     "RageTheatreSVideoPort"    # <i>
            #Option     "TunerType"             # <i>
            #Option     "RageTheatreMicrocPath"    # <str>
            #Option     "RageTheatreMicrocType"    # <str>
            #Option     "ScalerWidth"           # <i>
            #Option     "RenderAccel"           # [<bool>]
            #Option     "SubPixelOrder"         # [<str>]
            #Option     "ShowCache"             # [<bool>]
            #Option     "ClockGating"           # [<bool>]
            #Option     "VGAAccess"             # [<bool>]
            #Option     "ReverseDDC"            # [<bool>]
            #Option     "LVDSProbePLL"          # [<bool>]
            #Option     "AccelMethod"           # <str>
            #Option     "DRI"                   # [<bool>]
            #Option     "ConnectorTable"        # <str>
            #Option     "DefaultConnectorTable"    # [<bool>]
            #Option     "DefaultTMDSPLL"        # [<bool>]
            #Option     "TVDACLoadDetect"       # [<bool>]
            #Option     "ForceTVOut"            # [<bool>]
            #Option     "TVStandard"            # <str>
            #Option     "IgnoreLidStatus"       # [<bool>]
            #Option     "DefaultTVDACAdj"       # [<bool>]
            #Option     "Int10"                 # [<bool>]
            #Option     "EXAVSync"              # [<bool>]
            #Option     "ATOMTVOut"             # [<bool>]
            #Option     "R4xxATOM"              # [<bool>]
            #Option     "ForceLowPowerMode"     # [<bool>]
            #Option     "DynamicPM"             # [<bool>]
       Identifier  "Card0"
       Driver      "vesa"
       VendorName  "ATI Technologies Inc"
       BoardName   "Radeon X1650 Pro"
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

Espero cachis bien como solucionarlo.

Saludos.

---

### Post by Carlos C on 2010-01-27
¿y cómo instalaste el driver?

---

### Post by krackmu on 2010-01-28
> **Carlos C said:**
> ¿y cómo instalaste el driver?

por consola. Y si es posible desinstalarlo, me gustaria hacerlo tambien.

---

### Post by Carlos C on 2010-01-29
Eso depende, debes decirnos los pasos que utilizaste para instalarlo, la versión del driver, todo.

---

### Post by krackmu on 2010-01-29
> **Carlos C said:**
> Eso depende, debes decirnos los pasos que utilizaste para instalarlo, la versión del driver, todo.

bueno, basicamente abri la consola (ahi en el menu aplicaciones), y ejecute el archivo.run con sudo sh ./xxxxxxx.run la version del driver era la 8.4 creo (casi seguro.

y eso, cuando reinicie, queda la pantalla negra.

mira, te dejo el Xorg.0.log para que le hechen una miradita, ahi debe salir todo, pero yo no entiendo mucho lo que sale.

[http://pastebin.com/m1992312f]("http://pastebin.com/m1992312f")

Saludos.

---

### Post by Carlos C on 2010-02-02
No me queda claro cuál driver instalaste ni si lo compilaste o no, por lo tanto no puedo hablar de este caso en particular. Si compilaste el driver a partir de una fuente tienes que leer el readme y ver si existe un make uninstall.

---

### Post by krackmu on 2010-02-02
> **Carlos C said:**
> No me queda claro cuál driver instalaste ni si lo compilaste o no, por lo tanto no puedo hablar de este caso en particular. Si compilaste el driver a partir de una fuente tienes que leer el readme y ver si existe un make uninstall.

ya, no importa, si pasó tanto tiempo sin que lo pudiese arreglar que termine formateandolo. NO me van a creer, pero quedo mejor, no se pq.

Saludos y gracias por tomarse el tiempo.

---

