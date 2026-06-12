---
title: "Error con iDesk en Openbox"
date: 2009-01-10
forum: Software
---

### Post by Terraman on 2009-01-10
Hola a todos,

Tengo una vieja notebook (ver especificaciones en firma) a la cual le instalé el comando de línea de Ubuntu 8.04 y le he instalado software adicional que utliza pocos recursos. Utilizo Openbox como entonro de pantalla y le quiero instalar iDesk para tener íconos en el escritorio. Pero me aparece el siguiente error al tratar de correrlo en una terminal:

"terminate called after throwing an instance of'std::ios_base::failure' what(): basic_filebuf::underflow error reading file
Aborted"

Este es mi archivo .ideskrc en $HOME:

table Config
FontName: tahoma
FontSize: 8
FontColor: #ffffff
ToolTip.FontSize: 9
ToolTip.FontName: gothic
ToolTip.ForeColor: #0000FF
ToolTip.BackColor: #FFFFFF
ToolTip.CaptionOnHover: true
ToolTip.CaptionPlacement: right
Locked: false
Transparency: 100
Shadow: true
ShadowColor: #000000
ShadowX: 1
ShadowY: 2
Bold: false
ClickDelay: 300
IconSnap: true
SnapWidth: 55
SnapHeight: 100
SnapOrigin: BottomRight
SnapShadow: true
SnapShadowTrans: 200
CaptionOnHover: false
FillStyle: FillHLine
Background.File:
Background.Delay: 20
Background.Source: /home/herman/.wallpaper
Background.Mode: Scale
Background.Color: #C2CCFF
end
table Actions
Lock: right doubleClk
Drag: left hold
EndDrag: left singleClk
Execute[0]: left doubleClk
Execute[1}: right doubleClk
end

El siguiente es mi archivo de íconos en el directorio .idesktop en $HOME.

table Icon
Caption: File Manager
Command[0]: pcmanfm
Command[1]: pcmanfm
Icon: /usr/share/fbpanel/images/file-manager.png
X: 100
Y: 50
end

¿Aguien me podrá ayudar?

Desde ya muchas gracias,

---

### Post by Terraman on 2009-01-12
Hola, ¿alguien?

---

