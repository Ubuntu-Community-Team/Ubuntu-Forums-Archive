---
title: "ScITE listed twice in the Ubuntu Software Center"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bastones on 2012-01-20
Hi,

I upgraded my 11.10 installation to 12.04 (Alpha and all, it is quite stable). I had the ScITE text editor installed in 11.10 which wasn't still installed after upgrading to 12.04. However, going to the Ubuntu Software Center to reinstall it yields the same text editor listed twice. So I went ahead and installed it, and searching for it in the Dash returns two ScITE applications, but it appears one of them is merely a link to the scite executable.

Can anyone confirm whether they have ScITE listed twice in the Ubuntu Software Center? Is there something specific I can do to prevent this occurring each and every time I install ScITE?

Thanks,
Ben.

---

### Post by mc4man on 2012-01-20
It's listed twice because the app installs 2 .desktops, scite.desktop & SciTe.desktop

Additionally there are 2 files installed to /usr/bin, scite, which is the binary & SciTe which links to scite.

The SciTE.desktop contains a MimeTypes=text/plain; & on the Categories=  line adds TextEditor;
The purpose there I suppose is to have a separate "scite" that can be set as default for text files and or be available thru the context menu.

If it really bothers you then remove one of the .desktops from /usr/share/applications, which one your pick, I'd guess scite.desktop makes most sense


What really should of been done is possibly give the 2 .desktops a different Name= which you can do

Edit: the "TextEditor" category doesn't appear to be used in unity's app lens filter results, Utility; should be added to show under accessories, though both Scites do show under the Developer filter

---

### Post by Sworddragon on 2012-01-20
I have opened over 2 weeks ago already a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/scite/+bug/911126](https://bugs.launchpad.net/ubuntu/+source/scite/+bug/911126)

---

### Post by mc4man on 2012-01-20
Giving it a little thought, can't quite see the value of scite.desktop, though there might be.
If you want to keep both & separate them some suggested changes, line(s) changed marked in blue, es not my lang?

```
sudo gedit /usr/share/applications/scite.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
[COLOR="Blue"]Name=SciTE Programming Editor[/COLOR]
[COLOR="Blue"]Name[en_GB]=Scite Programming Editor[/COLOR]
[COLOR="Blue"]Name[es]=Editor de programación SciTE[/COLOR]
Comment=Programming editor
Comment[en_GB]=Programming editor
Comment[es]=Edita especializado para programación
Exec=scite %F
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/Sci48M.png
Categories=Application;Development;
```

```
sudo gedit /usr/share/applications/SciTE.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=SciTE Text Editor
Name[es]=Editor de textos SciTE
Name[fr]=Éditeur de texte SciTE
Name[ru]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1099;&#1081; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; SciTE
Comment=Edit your source files
Comment[es]=Edita especializado para programación
Comment[fr]=Éditer des fichiers sources
Comment[ru]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1093; &#1082;&#1086;&#1076;&#1086;&#1074;
GenericName=Text Editor
Type=Application
Exec=SciTE %F
Icon=Sci48M.png
Terminal=false
StartupNotify=true
[COLOR="Blue"]Categories=TextEditor;GTK;Application;Utility;[/COLOR]
MimeType=text/plain;
```

---

### Post by bastones on 2012-01-20
> **Sworddragon said:**
> I have opened over 2 weeks ago already a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/scite/+bug/911126](https://bugs.launchpad.net/ubuntu/+source/scite/+bug/911126)

Ah, cheers. Confirmed there I have the same issue :).

---

