---
title: "Problema de cambio de entorno"
date: 2010-04-04
forum: Software
---

### Post by Iced_R on 2010-04-04
Holas a todos!!

Tengo un pequeño problema con lo q tiene relación con el cambio de entorno (cambiar de Gnome a LXDE, por ejemplo). Tengo configurado Ubuntu para que me entre automáticamente sin pedir contraseña, pero cuando cierro la sesión de GNOME a mano, y después intento ingresar a alguna otra (estoy intentando hacerme un escritorio con fluxbox y un par de screenlets que encontré interesantes) simplemente no me aparecen las opciones de abajo, esas que tienen relación precisamente con el entorno que levantaré. Si alguien sabe cómo arreglar eso...

Ah, por si acaso pego mi xorg.conf:

```
Section "Device"
Identifier "Configured Video Device"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic CRT Display"
Modelname "CRT 1024x768"
Horizsync 30-63
Vertrefresh 56 - 71
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Gamma 1.0
# modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
# modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
# modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
# modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
# modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
Option "PreferredMode" "1024x768"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

---

