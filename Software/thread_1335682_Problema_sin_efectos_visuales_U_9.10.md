---
title: "Problema: sin efectos visuales U 9.10"
date: 2009-11-23
forum: Software
---

### Post by KAROLITO9 on 2009-11-23
Hola ese es mi problema, desde que actualice a  la vercion  8.04. se que mi tarjeta res muy vieja pero con la veciones anteriores DE UBUNTU, es decir 7.04 Y 7.10 funcionaba de lo mAS BIEN.


miren la targeta es una intel 845 G GEm segun el HARDINFO; 

-Display-
Resolution        : 1280x1024 pixels
Vendor        : The X.Org Foundation
Version        : 1.6.4
-Monitors-
Monitor 0        : 1280x1024 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Tungsten Graphics, Inc
Renderer        : Mesa DRI Intel(R) 845G GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
Version        : 1.3 Mesa 7.6
Direct Rendering        : Yes



y en el compiz:

Comando: $sudo gedit /usr/bin/compiz



FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T


intente comentando la linea:
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)


pero desaparece todo del escritorio, quedandoce pegado el equipo. y al intentar descomentar los demas campos pasa lo mismo.

tambien he intentado con:

con el .sh  gurdado como : compiz.sh

#!/bin/sh
SKIP_CHECKS=yes compiz --replace

pero nada...pasa lo mismo. escritorio sin menus y en blanco.


alguna solucion.

DE ANTEMANO MUCHAS GRACIAS.

---

