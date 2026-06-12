---
title: "Little Help from the Thunderbird users please"
date: 2010-05-15
forum: The Cafe
---

### Post by Excedio on 2010-05-15
In an effort to get Thunderbird integrated to my Indicator Applet better, I messed up a file. Can someone that has Thunderbird please go to the terminal and type in:

```
sudo gedit /usr/share/applications/thunderbird.desktop
```When the file opens up, please copy and paste the contents here. Thanks.

---

### Post by Uzi304 on 2010-05-15
```
[Desktop Entry]
Name=Thunderbird
Comment=Mail & News Reader
GenericName=Mail Client & News Reader
Exec=thunderbird
Icon=thunderbird
Terminal=false
Type=Application
Categories=Network;Email;
StartupNotify=true
```

---

### Post by Excedio on 2010-05-15
> **Uzi304 said:**
> ```
[Desktop Entry]
Name=Thunderbird
Comment=Mail & News Reader
GenericName=Mail Client & News Reader
Exec=thunderbird
Icon=thunderbird
Terminal=false
Type=Application
Categories=Network;Email;
StartupNotify=true
```

Thanks. That was all it had? Odd.. my original file was a lot longer. Anyone else have more than this?

---

### Post by alket on 2010-05-15
> [Desktop Entry]
Encoding=UTF-8
Name=Mozilla Thunderbird Mail/News
Comment=Read/Write Mail/News with Mozilla Thunderbird
GenericName=Mail Client
Exec=thunderbird %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
Categories=Application;Network;Email;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;
StartupWMClass=Thunderbird-bin
StartupNotify=true
Name[es]=Cliente de correo y noticias Thunderbird
Name[cs]=Po&#353;tovní klient Thunderbird
Name[ca]=Client de correu Thunderbird
Name[fi]=Thunderbird-sähköposti
Name[fr]=Messagerie Thunderbird
Name[hu]=Thunderbird levelez&#337;kliens
Name[pl]=Klient poczty Thunderbird
Name[pt_BR]=Cliente de E-mail Thunderbird
Name[sv]=E-postklienten Thunderbird
Comment[es]=Lea y escriba correos y noticias con Mozilla Thunderbird
Comment[ca]=Llegiu i escriviu correu
Comment[cs]=&#268;tení a psaní po&#353;ty
Comment[de]=Emails lesen und verfassen
Comment[fi]=Lue ja kirjoita sähköposteja
Comment[fr]=Lire et écrire des courriels
Comment[hu]=Levelek írása és olvasása a Thunderbirddel
Comment[it]=Leggere e scrivere email
Comment[ja]=&#12513;&#12540;&#12523;&#12398;&#35501;&#12415;&#26360;&#12365;
Comment[pl]=Czytanie i wysy&#322;anie e-maili
Comment[pt_BR]=Ler e escrever suas mensagens
Comment[sv]=Läs och skriv e-post
GenericName[hu]=Levelez&#337;kliens
I recommend you to install MinimizeToTray Plus instead of indicator applet.

---

### Post by Excedio on 2010-05-15
> **babaroga said:**
> I recommend you to install MinimizeToTray Plus instead of indicator applet.

I appreciate and respect your recommendation, but that's not what I was asking for.

However, you have the information I was looking for :-D

THANKS!

---

