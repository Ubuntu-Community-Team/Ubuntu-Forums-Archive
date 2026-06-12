---
title: "Sin efectos a activar el cubo"
date: 2009-08-18
forum: Software
---

### Post by Chogogo on 2009-08-18
Hola.
Me acabo de pasar a ubuntu 9.04 y utilizo una PC Hp pavillion con una targeta de Video nVidida GeForce 8400GE y el driver instalado con Envyng. Con mi sistema anterior la cosa funcionaba bien y la instalación del driver la hice de la misma forma. Los Efectos de escritorio funcionaban junto con el escritorio extendido en mis dos monitores y el cubo aparecia y rotaba sin problemas. Ahora con 9.04 quiero hacer lo mismo. La cosa funciona hasta cuando trato de activar el pluggin de el cubo. Enseguida me quedo sin efectos 3D. No recibo ningun mensaje de error ni nada, solo me quedo sin efectos. y si lo desctivo regresan los efectos. El problema parece ser con este pluggin de compiz (quisas con algunos otros tambien), pues he probado otros y funcionana bien. 

Alguna sugerencia, idea...Gracias de Antemano por la colaboración.
Aqui les dejo mi Xorg (generado por nVidia-Settings)

Saludos y que Dios los bendiga.
==================XORG.CONF=====================================
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
      Disable	"dri2"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IBM G72"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1024x768 +1600+0, DFP: 1600x1024 +0+0; CRT: NULL, DFP: 1600x1024 +0+0; CRT: NULL, DFP: 1440x900 +0+0; CRT: NULL, DFP: 1440x900_60 +0+0; CRT: NULL, DFP: 1360x768 +0+0; CRT: NULL, DFP: 1360x768_60_0 +0+0; CRT: NULL, DFP: 1280x1024 +0+0; CRT: NULL, DFP: 1280x1024_60 +0+0; CRT: NULL, DFP: 1280x960 +0+0; CRT: NULL, DFP: 1280x720 +0+0; CRT: NULL, DFP: 1152x864 +0+0; CRT: NULL, DFP: 1152x864_75_0 +0+0; CRT: NULL, DFP: 1152x864_70 +0+0; CRT: NULL, DFP: 1152x864_60 +0+0; CRT: NULL, DFP: 1024x768 +0+0; CRT: NULL, DFP: 1024x768_70 +0+0; CRT: NULL, DFP: 1024x768_60 +0+0; CRT: NULL, DFP: 960x600 +0+0; CRT: NULL, DFP: 960x540 +0+0; CRT: NULL, DFP: 896x672 +0+0; CRT: NULL, DFP: 840x525 +0+0; CRT: NULL, DFP: 840x525d70 +0+0; CRT: NULL, DFP: 840x525d60 +0+0; CRT: NULL, DFP: 840x525d60_0 +0+0; CRT: NULL, DFP: 832x624 +0+0; CRT: NULL, DFP: 800x600 +0+0; CRT: NULL, DFP: 800x600_72 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by nopersona on 2009-08-18
Revisa los permisos de tu usuario, confirma que tiene asiganada la aceleración 3d. También instala fusión icon. Algún otro problema con 3d, o solo compiz?

---

### Post by Chogogo on 2009-08-19
> **nopersona said:**
> Revisa los permisos de tu usuario, confirma que tiene asiganada la aceleración 3d. También instala fusión icon. Algún otro problema con 3d, o solo compiz?

Hola. ya tengo instalado Fusion-Icon. Solo tengo problemas con algunos Pluggins de Compiz. Por ejemplo el "desktop-Ring" funciona bien. El Cubo es el que presenta problemas ( pero a lo mejor algun otro tambien, no los he revisado todos). No he notado ningun otro problema relacionado con 3D

Podrias decirme como verifico lo de los permisos de Usuario?

Gacias...Y que Dios los bendiga

---

### Post by Chogogo on 2009-08-25
Hola...Ejecute Compiz desde la terminal y esto fué lo que obtuve

===========================================
omar@Hogar:~$ compiz.real
compiz.real (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real (core) - Fatal: No manageable screens found on display :0.0
omar@Hogar:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2624x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
^C*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x09b252a8 ***
=======================================

realmente extraño que cuando lo ejecute desde Fusion Icon, funciona correctamente (en apariencia). con efectos y hasta con varios pluggins, es solo el "Cubo" el que me deja sin efectos...pero incluso, aun sin efectos, el cubo aparece y "funciona"...pero todo se vuelve superlento.

Gracias, un abrazo y que Dios los bendiga.

---

