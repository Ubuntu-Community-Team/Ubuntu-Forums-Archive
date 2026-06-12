---
title: "Ardour link is broken after upgrade"
date: 2016-08-27
forum: Ubuntu Studio
---

### Post by noxinespresso on 2016-08-27
Hi all, 

On Ubuntu Studio 16. I noticed after upgrading Ardour, the Ardour link in the menu is broken. I can still do the run ardour command, but I was wondering how to fix the link. Here is a screenshot of the error.

[ATTACH=CONFIG]270898[/ATTACH]

Thanks for the help!

---

### Post by Alexandre_Peccioli on 2016-08-29
If you upgraded to Ardour 5 by repositories kxstudio?

Come in to usr/share/applications and delete the file Ardour 4.

After this copy the following text in I text editor and save it in the same folder with the name of ardour.desktop:
```

[Desktop Entry]
Name=Ardour
Comment=Ardour Digital Audio Workstation
Exec=/usr/bin/ardour
Icon=/opt/ardour/share/icons/ardour-app-icon_osx.png
Terminal=false
MimeType=application/x-ardour;
Type=Application
Categories=AudioVideo;Audio;AudioEditing;X-Recorders;X-Multitrack;X-Jack;

```
You have to check whether the Exec and Icon lines are correct for your computer because they can vary from one installation to another.

---

