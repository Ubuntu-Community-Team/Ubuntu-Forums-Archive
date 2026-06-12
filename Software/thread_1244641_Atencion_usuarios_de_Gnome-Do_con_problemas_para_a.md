---
title: "Atencion usuarios de Gnome-Do con problemas para abrir su carpeta home"
date: 2009-08-19
forum: Software
---

### Post by augias on 2009-08-19
A mi me ocurría, y he visto que es un problema generalizado, que abrir la carpeta Home en nautilus usando gnome-do no funcionaba, mientras que abrir subcarpetas dentro de Home no era un problema. 

Si te ocurre lo mismo, se puede arreglar facilmente:
```
sudo nano /usr/share/applications/nautilus-home.desktop 

```

> [Desktop Entry]
Encoding=UTF-8
Name=Home Folder
Comment=Open your personal folder
TryExec=nautilus
Exec=nautilus --no-desktop
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus


Agrega un espacio y un punto despues de 'Exec=nautilus --no-desktop' para que diga 'Exec=nautilus --no-desktop .'

Guarda con ctrl+o, sale con ctrl+x y listo. Yo hice un logout rapidito y listo!

No sé si el problema ocurrirá en KDE o XFCE también. Ojala haya podido ayudar mis amigos en gnome-do!

Augías.

---

### Post by mjota on 2009-11-06
Ha ido perfectamente, muchas gracias!

---

### Post by Carlos C on 2009-11-08
mjota, ¿con qué versión de Ubuntu te sirvió esta solución?
Saludos.

---

### Post by RafaelG on 2009-11-08
Gracias Men trabaja perfecto en mi versio Karmic Koala

---

