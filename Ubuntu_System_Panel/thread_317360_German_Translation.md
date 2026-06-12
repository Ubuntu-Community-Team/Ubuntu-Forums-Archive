---
title: "German Translation"
date: 2006-12-12
forum: Ubuntu System Panel
---

### Post by vitae on 2006-12-12
Hello everybody,

actually i am using gentoo. i was trying out slab and now usp. i have to say that plugin thing is very useful.

due the fact i am german and there is no german translation i created a potfile. two gaps are missing, but i hope someone will fit it.

de_DE.po

```
msgid ""
msgstr ""
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Orte"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Anwendungen"

#: usp.glade:247
msgid "Settings"
msgstr "Einstellungen"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Administration"

#: usp.glade:663
msgid "Install Software"
msgstr "Software installieren"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Kontrollzentrum"

#: usp.glade:788
msgid "Lock screen"
msgstr "Bildschirm sperren"

#: usp.glade:852
msgid "Quit..."
msgstr "Abmelden..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Computer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Alle Programme</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Alle Programme"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Zubehör</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Spiele</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafik</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Büro</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programmieren</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Sound und Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Systemverwaltung</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Einstellungen</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Alle</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Mehr Programme...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr ""

#: usp.glade:2216
msgid "Search"
msgstr "Suchen"

#: usp.glade:2516
msgid "Network"
msgstr "Netzwerk"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Datum und Uhrzeit"

#: usp.glade:2764
msgid "Theme"
msgstr "Thema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Bildschirmauflösung"

#: usp.glade:3037
msgid "Configure your system"
msgstr "System konfigurieren"

#: usp.glade:3133
msgid "Move up"
msgstr "Nach oben"

#: usp.glade:3142
msgid "Move down"
msgstr "Nach unten"

#: usp.glade:3151
msgid "Edit labels"
msgstr ""

#: usp.glade:3160
msgid "Insert separator"
msgstr "Trennlinie einfügen"

#: usp.glade:3169
msgid "Insert space"
msgstr "Platz einfügen"

#: usp.glade:3178
msgid "Remove"
msgstr "Entfernen"

#: usp.glade:3187
msgid "Edit item"
msgstr "Objekt bearbeiten"

#: usp.glade:3256
msgid "Name"
msgstr "Name"

#: usp.glade:3300
msgid "Generic name"
msgstr ""

#: usp.glade:3343
msgid "Comment"
msgstr "Kommentar"

#: usp.glade:3386
msgid "Exec"
msgstr "Ausführen"

#: usp.glade:3429
msgid "Icon"
msgstr "Icon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Zu Favoriten hinzufügen"
```

i hope nobody is angry that i wrote it here. i didn`t find the cvs page of the author nor an translation page.

perhaps one suggestion:

the most thing that i would like to see is a way to tell the USP its height. 

greetings 

i am looking forward to a new version

vitae

---

### Post by Malac on 2006-12-13
Hi vitae,

You could try my GITOI application to create a translated glade file.
It's available here as a .tar or .deb:
[http://www.ubuntuforums.org/showthread.php?t=262139](http://www.ubuntuforums.org/showthread.php?t=262139)

I'm still looking for testers to see if this app is useful to people.

Hope this helps, Malac.

---

### Post by vitae on 2006-12-15
well i don`t know very much about glade. i thought a .po file is actually the translation.

if you need that glade file i will translate it when i have a lil bit time.

thnx 4 answer :)

---

### Post by vitae on 2006-12-19
plugin4.gitoi
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Computer|>Computer<|
Network|>Netzwerk<|
Date and Time|>Datum und Uhrzeit<|
Theme|>Thema<|
Screen Resolution|>Bildschirmauflösung<|
Control Center|>Kontrollzentrum<|
Configure your system|>Systemeinstellungen<|

```

usp.gitoi
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
label42|><|
Install Software|>Software installieren<|
Control Center|>Kontrollzentrum<|
Lock screen|>Bildschirm sperren<|
Quit...|>Beenden<|
&lt;span size=&quot;small&quot;&gt;Alle Programme&lt;/span&gt;|><|
label78|><|
&lt;span size=&quot;small&quot;&gt; Programme&lt;/span&gt;|><|
&lt;span size=&quot;small&quot;&gt; Alle&lt;/span&gt;|><|
label100|><|
&lt;span weight=&quot;bold&quot;&gt;Mehr Programme&lt;/span&gt;|><|
Move up|>Nach oben<|
Move down|>Nach unten<|
Edit|>Bearbeiten<|
Insert separator|>Trennlinie einfügen<|
Insert space|>Platz einfügen<|
Remove|>Entfernen<|
Name|>Name<|
Generic name|><|
Comment|>Kommentar<|
Exec|>Ausführen<|
Icon|>Icon<|
Add to favourites|>Zu Favoriten hinzufügen<|
```

USPcalrem.gitoi
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Tasks|>Aufgaben<|
Appointments|>Verabredungen<|

```

USPnotes.gitoi
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Filename : |>Dateiname<|
```

USPuser.gitoi
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
User|>Benutzer<|
```

Well, there are 2 i think translations missing. I hope they can be integrated in a new release.

To GITOI. It is a nice app. So i don`t have to search in the glade files. The only thing i was missing is that if i load a new glade that the old 2 right windows are not refreshed. that was a little bit irritating.

greetings
vitae

p.s.: in the system_management there are buttons like software install, etc. may it be possible to be able as user to change them? on gentoo, we usually install software not with a package manager, so the button is quite useless for us.

---

