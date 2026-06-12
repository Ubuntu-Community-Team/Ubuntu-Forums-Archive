---
title: "[Theme] Winter Mist -  Released!!!"
date: 2022-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by Perfect Storm on 2022-07-31
[img]https://user-images.githubusercontent.com/60283532/182013491-1c10b36e-3f14-4118-bfd2-e853d374ddf9.png[/img]

A flat grey/white theme suite for Gnome, XFCE and Budie DE.
Tested on Fedora Workstation, Zorin OS 16 Pro/core & lite.

Video
--------
[video=youtube;JVhp8UV7d9I]https://www.youtube.com/watch?v=JVhp8UV7d9I[/video]

Screenshots
-----------------
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290792&stc=1&d=1659298184[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290793&stc=1&d=1659298184[/IMG]

Download
---------------
[https://www.gnome-look.org/p/1870058](https://www.gnome-look.org/p/1870058)

[https://github.com/SethStormR/Winter-Mist](https://github.com/SethStormR/Winter-Mist)

---

### Post by #&amp;thj^% on 2022-07-31
Arch, Plasma 5.25.3

---

### Post by Perfect Storm on 2022-07-31
> **1fallen said:**
> Arch, Plasma 5.25.3

That's the reason I don't release for KDE. On all other DE/WMs the icons looks as they should, but not on KDE for some reason. :(

---

### Post by Perfect Storm on 2022-07-31
> **1fallen said:**
> Arch, Plasma 5.25.3

I have been asking around and for what they said making icons for KDE is a pain the rear. But I have made some extra coding into the index file which hopeful will solve it.
If you want to test it for me: [https://mega.nz/file/5FoShRpD#YLoAsXTnj-N2xR4e2xqNYUnmasIt_UGN3pB0B_35k7U](https://mega.nz/file/5FoShRpD#YLoAsXTnj-N2xR4e2xqNYUnmasIt_UGN3pB0B_35k7U)

---

### Post by #&amp;thj^% on 2022-08-01
> **Perfect Storm said:**
> I have been asking around and for what they said making icons for KDE is a pain the rear. But I have made some extra coding into the index file which hopeful will solve it.
If you want to test it for me: [https://mega.nz/file/5FoShRpD#YLoAsXTnj-N2xR4e2xqNYUnmasIt_UGN3pB0B_35k7U](https://mega.nz/file/5FoShRpD#YLoAsXTnj-N2xR4e2xqNYUnmasIt_UGN3pB0B_35k7U)
Yep KDE is a royal pain in the caboose: ;)
Happy to test it for you/me..

---

### Post by Perfect Storm on 2022-08-01
I'm baffled...

I've also looked at others work to see what I'm doing wrong.

---

### Post by #&amp;thj^% on 2022-08-01
Perfect Storm, You did not ask for my help but, in short KDE uses freedesktop.org compliant icon themes. These consist of a directory structure divided into categories (e.g. applications, places, actions, emblems... probably others I can't think of off hand), and also divided into icon sizes (e.g. 48x48, 128x128, etc). You can also make scalable icons (some icon themes have both)
I'm not sure how old this one is, and you may have looked here before now: [https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)

But doesn't actually matter what they're called because they are all defined in the configuration file (which is (usually, always?) called index.theme).
I did not see that in your theme folder "index.theme"
Here is just an example from an existing "index"
```
[Icon Theme]
Name=Oxygen Zion
Name[ar]=&#1571;&#1603;&#1587;&#1580;&#1610;&#1606; &#1586;&#1610;&#1608;&#1606;
Name[az]=Oxygen Zion
Name[bg]=Oxygen &#1094;&#1080;&#1072;&#1085;
Name[ca]=Oxygen Zion
Name[ca@valencia]=Oxygen Zion
Name[cs]=Oxygen Zion
Name[da]=Oxygen Zion
Name[de]=Oxygen-Zion
Name[el]=Oxygen Zion
Name[en_GB]=Oxygen Zion
Name[es]=Oxígeno Sión
Name[et]=Oxygen Zion
Name[eu]=Oxygen Zion
Name[fi]=Oxygen Zion
Name[fr]=Oxygen Zion
Name[gl]=Oxygen Zion
Name[hu]=Oxygen Zion
Name[ia]=Oxygen Zion
Name[id]=Zion Oxygen
Name[it]=Oxygen Zion
Name[ko]=Oxygen &#51648;&#50728;
Name[lt]=Oxygen Sioninis
Name[nl]=Oxygen zion
Name[nn]=Oxygen zion
Name[pa]=&#2566;&#2581;&#2616;&#2624;&#2588;&#2600; &#2651;&#2624;&#2566;&#2600;
Name[pl]=Syjo&#324;ski Tlen
Name[pt]=Oxygen Sião
Name[pt_BR]=Oxygen Zion
Name[ro]=Oxygen Zion
Name[ru]=Oxygen Zion
Name[sk]=Kyslík Zion
Name[sl]=Kisik - Zion
Name[sr]=&#1050;&#1080;&#1089;&#1077;&#1086;&#1085;&#1080;&#1082;&#1086;&#1074; &#1089;&#1080;&#1086;&#1085;
Name[sr@ijekavian]=&#1050;&#1080;&#1089;&#1077;&#1086;&#1085;&#1080;&#1082;&#1086;&#1074; &#1089;&#1080;&#1086;&#1085;
Name[sr@ijekavianlatin]=Kiseonikov sion
Name[sr@latin]=Kiseonikov sion
Name[sv]=Oxygen Zion
Name[tg]=&#1054;&#1082;&#1089;&#1080;&#1075;&#1077;&#1085;&#1080; &#1057;&#1080;&#1086;&#1085;
Name[tr]=Oksijen Gö&#287;ü
Name[uk]=Oxygen Zion
Name[x-test]=xxOxygen Zionxx
Name[zh_CN]=Oxygen &#36731;&#27687;&#38177;&#23433;
Name[zh_TW]=Oxygen Zion
Comment=Oxygen mouse theme. Oxygenize your desktop!
Comment[ar]=&#1587;&#1605;&#1577; &#1571;&#1603;&#1587;&#1580;&#1610;&#1606; &#1604;&#1604;&#1601;&#1571;&#1585;&#1577;. &#1571;&#1603;&#1587;&#1606; &#1587;&#1591;&#1581; &#1605;&#1603;&#1578;&#1576;&#1603;!
Comment[az]=Oxygen kursor görünü&#351;ü toplusu.
Comment[bg]=Oxygen &#1090;&#1077;&#1084;&#1072; &#1079;&#1072; &#1084;&#1080;&#1096;&#1082;&#1072;&#1090;&#1072;. &#1054;&#1082;&#1089;&#1080;&#1075;&#1077;&#1085;&#1080;&#1088;&#1072;&#1081;&#1090;&#1077; &#1074;&#1072;&#1096;&#1072;&#1090;&#1072; &#1088;&#1072;&#1073;&#1086;&#1090;&#1085;&#1072; &#1089;&#1088;&#1077;&#1076;&#1072;!
Comment[ca]=Tema Oxygen per al ratolí. Oxigena el teu escriptori!
Comment[ca@valencia]=Tema Oxygen per al ratolí. Oxigena el teu escriptori!
Comment[da]=Oxygen musetema. Oxygenisér din desktop!
Comment[de]=Mausdesign für Oxygen.
Comment[el]=&#920;&#941;&#956;&#945; &#960;&#959;&#957;&#964;&#953;&#954;&#953;&#959;&#973; Oxygen. &#922;&#940;&#957;&#964;&#949; &#964;&#951;&#957; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962; &#963;&#945;&#962; &#960;&#953;&#959; Oxygen!
Comment[en_GB]=Oxygen mouse theme. Oxygenise your desktop!
Comment[es]=Tema de ratón Oxígeno. ¡Oxigene su escritorio!
Comment[et]=Oxygeni hiireteema. Oksigeneeri oma töölaud!
Comment[eu]=Oxygen sagu-gaia, Oxygenotu zure mahaigaina!
Comment[fi]=Oxygen-osoitinteema. Oxygenoi työpöytäsi!
Comment[fr]=Thème de curseur «*Oxygen*». Oxygénez votre bureau*!
Comment[gl]=Tema de rato de Oxygen. Oxixene o escritorio!
Comment[hu]=Oxygen egértéma. Lélegezzen fel asztala!
Comment[ia]=Thema de mus de Oxygen. Oxygenisa tu scriptorio!
Comment[id]=Tema mouse Oxygen. Mengoksigenkan desktopmu!
Comment[it]=Tema del mouse Oxygen. Ossigena il tuo desktop!
Comment[ko]=Oxygen &#47560;&#50864;&#49828; &#53580;&#47560;&#51077;&#45768;&#45796;. &#45936;&#49828;&#53356;&#53681;&#50640; &#49328;&#49548;&#47484; &#48520;&#50612;&#45347;&#51004;&#49901;&#49884;&#50724;!
Comment[lt]=Oxygen pel&#279;s apipavidalinimas. Papuo&#353;kite savo darbalauk&#303; naudodami Oxygen!
Comment[nl]=Muisthema van Oxygen. Geef uw bureaublad zuurstof!
Comment[nn]=Oxygen peikartema. Oxygeniser skrivebordet!
Comment[pa]=&#2566;&#2581;&#2616;&#2624;&#2588;&#2600; &#2606;&#2622;&#2570;&#2616; &#2597;&#2624;&#2606;&#2404; &#2566;&#2581;&#2616;&#2624;&#2588;&#2600; &#2600;&#2622;&#2610; &#2596;&#2625;&#2617;&#2622;&#2593;&#2622; &#2593;&#2632;&#2616;&#2581;&#2591;&#2622;&#2602;!
Comment[pl]=Tlen - zestaw wska&#378;ników myszy. Dotle&#324; swój pulpit!
Comment[pt]=Tema do rato no Oxygen. Dê oxigénio ao seu ambiente de trabalho!
Comment[pt_BR]=Tema de cursor Oxygen. Oxygenize seu desktop!
Comment[ro]=Tematic&#259; pentru maus Oxygen. Oxigeneaz&#259;-&#539;i biroul!
Comment[ru]=&#1053;&#1072;&#1073;&#1086;&#1088; &#1082;&#1091;&#1088;&#1089;&#1086;&#1088;&#1086;&#1074; &#1084;&#1099;&#1096;&#1080; Oxygen
Comment[sk]=Vzh&#318;ad my&#353;i Kyslík. Okysli&#269;te si plochu!
Comment[sl]=Tema kazalke Kisik. Nasitite va&#353;e namizje s kisikom!
Comment[sr]=&#1050;&#1080;&#1089;&#1077;&#1086;&#1085;&#1080;&#1082;&#1086;&#1074;&#1072; &#1090;&#1077;&#1084;&#1072; &#1084;&#1080;&#1096;&#1072;. &#1044;&#1072; &#1074;&#1072;&#1084; &#1087;&#1086;&#1074;&#1088;&#1096; &#1087;&#1088;&#1086;&#1076;&#1080;&#1096;&#1077;!
Comment[sr@ijekavian]=&#1050;&#1080;&#1089;&#1077;&#1086;&#1085;&#1080;&#1082;&#1086;&#1074;&#1072; &#1090;&#1077;&#1084;&#1072; &#1084;&#1080;&#1096;&#1072;. &#1044;&#1072; &#1074;&#1072;&#1084; &#1087;&#1086;&#1074;&#1088;&#1096; &#1087;&#1088;&#1086;&#1076;&#1080;&#1096;&#1077;!
Comment[sr@ijekavianlatin]=Kiseonikova tema mi&#353;a. Da vam povr&#353; prodi&#353;e!
Comment[sr@latin]=Kiseonikova tema mi&#353;a. Da vam povr&#353; prodi&#353;e!
Comment[sv]=Oxygen-muspekartema. Syresätt skrivbordet!
Comment[tg]=&#1052;&#1072;&#1074;&#1079;&#1263;&#1080; &#1084;&#1091;&#1096;&#1080; &#1054;&#1082;&#1089;&#1080;&#1075;&#1077;&#1085;. &#1052;&#1080;&#1079;&#1080; &#1082;&#1086;&#1088;&#1080;&#1080; &#1093;&#1091;&#1076;&#1088;&#1086; &#1073;&#1072; &#1054;&#1082;&#1089;&#1080;&#1075;&#1077;&#1085; &#1075;&#1072;&#1088;&#1076;&#1086;&#1085;&#1077;&#1076;!
Comment[tr]=Oksijen fare temas&#305;. Masaüstünüzü Oksijenle&#351;tirin!
Comment[uk]=&#1058;&#1077;&#1084;&#1072; &#1074;&#1082;&#1072;&#1079;&#1110;&#1074;&#1085;&#1080;&#1082;&#1110;&#1074; &#1084;&#1080;&#1096;&#1110; Oxygen. &#1044;&#1086;&#1076;&#1072;&#1081;&#1090;&#1077; &#1082;&#1080;&#1089;&#1085;&#1102; &#1074;&#1072;&#1096;&#1110;&#1081; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110;!
Comment[x-test]=xxOxygen mouse theme. Oxygenize your desktop!xx
Comment[zh_CN]=Oxygen &#36731;&#27687;&#40736;&#26631;&#20027;&#39064;&#65292;&#35753;&#24744;&#30340;&#26700;&#38754;&#21628;&#21560;&#36731;&#27687;&#12290;
Comment[zh_TW]=Oxygen &#28369;&#40736;&#20027;&#38988;&#12290;

```
Oh brother, I'm going blind for sure, I found your index file.

---

### Post by Perfect Storm on 2022-08-01
It should contain an index files with my codes in it :-k

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290797&stc=1&d=1659376351[/IMG]

---

### Post by #&amp;thj^% on 2022-08-01
Yep as i said I'm going blind, I found it.
Some diff's I noticed:
Breeze Dark:
```
########## Directories
########## ordered by category and alphabetically

Directories=actions/12,actions/16,actions/22,actions/24,actions/32,actions/48,actions/64,animations/16,animations/22,apps/16,apps/22,apps/32,apps/48,preferences/22,preferences/32,applets/16,applets/22,applets/48,applets/64,applets/128,applets/256,categories/32,devices/16,devices/22,devices/64,emblems/8,emblems/16,emblems/22,emotes/22,mimetypes/16,mimetypes/22,mimetypes/32,mimetypes/64,places/16,places/22,places/32,places/48,places/96,places/64,status/16,status/22,status/24,status/32,status/48,status/64,actions/symbolic,devices/symbolic,emblems/symbolic,places/symbolic,status/symbolic
ScaledDirectories=actions/16@2x,actions/16@3x,actions/22@2x,actions/22@3x,actions/24@2x,actions/24@3x,actions/32@2x,actions/32@3x,animations/16@2x,animations/16@3x,apps/16@2x,apps/16@3x,apps/22@2x,apps/22@3x,devices/16@2x,devices/16@3x,devices/22@2x,devices/22@3x,emblems/16@2x,emblems/16@3x,emblems/22@2x,emblems/22@3x,emotes/22@2x,emotes/22@3x,mimetypes/16@2x,mimetypes/16@3x,mimetypes/22@2x,mimetypes/22@3x,places/16@2x,places/16@3x,places/22@2x,places/22@3x,status/16@2x,status/16@3x,status/22@2x,status/22@3x
```
Winter Mist test
```
Directories=actions/16,actions/scalable,apps/scalable,categories/scalable,devices/scalable,emblems/scalable,places/16,places/scalable,panel/22,mimetypes/scalable
``` 
And then ########## Actions
########## ordered by size

```
#12x12 - Fixed size - For Inkscape
[actions/12]
Size=12
Context=Actions
Type=Fixed

#16x16 - Fixed size - For use in sidebar(s) smaller toolbar(s) >!!!ONLY!!!<: e.g. Kate movable sidebar/toolbar (search and replace, current project, etc.) or Juk tree view - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/16]
Size=16
Context=Actions
Type=Fixed

#16x16@2x - Fixed size - For use in sidebar(s) smaller toolbar(s) >!!!ONLY!!!<: e.g. Kate movable sidebar/toolbar (search and replace, current project, etc.) or Juk tree view - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/16@2x]
Size=16
Scale=2
Context=Actions
Type=Fixed

#16x16@3x - Fixed size - For use in sidebar(s) smaller toolbar(s) >!!!ONLY!!!<: e.g. Kate movable sidebar/toolbar (search and replace, current project, etc.) or Juk tree view - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/16@3x]
Size=16
Scale=3
Context=Actions
Type=Fixed

#22x22 - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/22]
Size=22
Context=Actions
Type=Fixed

#22x22@2x - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/22@2x]
Size=22
Scale=2
Context=Actions
Type=Fixed

#22x22@3x - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/22@3x]
Size=22
Scale=3
Context=Actions
Type=Fixed

#24x24 - Fixed size - GTK icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/24]
Size=24
Context=Actions
Type=Fixed

#24x24@2x - Fixed size - GTK icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/24@2x]
Size=24
Scale=2
Context=Actions
Type=Fixed

#24x24@3x - Fixed size - GTK icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/24@3x]
Size=24
Scale=3
Context=Actions
Type=Fixed

#32x32 - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/32]
Size=32
Context=Actions
Type=Scalable
MinSize=32
MaxSize=256

#32x32@2x - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/32@2x]
Size=32
Scale=2
Context=Actions
Type=Scalable
MinSize=32
MaxSize=256

#32x32@3x - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/32@3x]
Size=32
Scale=3
Context=Actions
Type=Scalable
MinSize=32
MaxSize=256

#48x48 - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/48]
Size=48
Context=Actions
Type=Scalable
MinSize=48
MaxSize=256

#64x64 - Fixed size - For toolbar icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[actions/64]
Size=64
Context=Actions
Type=Scalable
MinSize=32
MaxSize=256

########## Animations
########## ordered by size

#16x16 - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[animations/16]
Size=16
Context=Animations
Type=Fixed

#16x16@2x - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[animations/16@2x]
Size=16
Scale=2
Context=Animations
Type=Fixed

#16x16@3x - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[animations/16@3x]
Size=16
Scale=3
Context=Animations
Type=Fixed

#22x22 - Scalable
[animations/22]
Size=22
Context=Animations
Type=Scalable
MinSize=22
MaxSize=256

########## Apps
########## ordered by size

#16x16 - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[apps/16]
Size=16
Context=Applications
Type=Fixed

#16x16@2x - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[apps/16@2x]
Size=16
Scale=2
Context=Applications
Type=Fixed

#16x16@3x - Fixed size - Application icon(s) for Dolphin sidebar - OPTIONAL + DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[apps/16@3x]
Size=16
Scale=3
Context=Applications
Type=Fixed

#22x22 - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. Dolphin Open Terminal/About Dolphin/About KDE buttons - WRONG_ICON_USAGE_BY_APP - Monochrome
[apps/22]
Size=22
Context=Applications
Type=Fixed

#22x22@2x - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. Dolphin Open Terminal/About Dolphin/About KDE buttons - WRONG_ICON_USAGE_BY_APP - Monochrome
[apps/22@2x]
Size=22
Scale=2
Context=Applications
Type=Fixed

#22x22@3x - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. Dolphin Open Terminal/About Dolphin/About KDE buttons - WRONG_ICON_USAGE_BY_APP - Monochrome
[apps/22@3x]
Size=22
Scale=3
Context=Applications
Type=Fixed

#32x32 - Fixed size - For System Settings icons >!!!ONLY!!!< - Scalable to the following sizes: 32x32 (default), 64x64, 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[apps/32]
Size=32
Context=Applications
Type=Fixed

#48x48 - Scalable - For application icons >!!!ONLY!!!< - Scalable to the following sizes: 48x48 (default), 96x96 and 24x24 (not recommended) - DO_NOT_USE_ANYWHERE_ELSE - Color
[apps/48]
Size=48
Context=Applications
Type=Scalable
MinSize=48
MaxSize=256

#32x32 - Scalable - For System Settings icons >!!!ONLY!!!< - Scalable to the following sizes: 32x32 (default), 64x64, 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[preferences/32]
Size=32
Context=Applications
Type=Scalable
MinSize=32
MaxSize=256

#22x22 - Fixed size - For System Settings icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[preferences/22]
Size=22
Context=Applications
Type=Fixed

#16x16 - Only used for car.svg, symlinked for KMyMoney
[applets/16]
Size=16
Context=Status
Type=Fixed

#256x256 - Color for applets
[applets/22]
Size=22
Context=Status
Type=Scalable
MinSize=22
MaxSize=256

#256x256 - Color for applets
[applets/48]
Size=48
Context=Status
Type=Scalable
MinSize=32
MaxSize=256

#256x256 - Animation icons for kwin desktop effects
[applets/64]
Size=64
Context=Status
Type=Scalable
MinSize=32
MaxSize=256

#256x256 - Color
[applets/128]
Size=128
Context=Applications
Type=Scalable
MinSize=32
MaxSize=256

#256x256 - Scalable - For applets / widgets icons >!!!ONLY!!! - DO_NOT_USE_ANYWHERE_ELSE - Color
[applets/256]
Size=256
Context=Applications
Type=Scalable
MinSize=48
MaxSize=256

########## Categories
########## ordered by size

#32x32 - Fixed size - For categories icons >!!!ONLY!!!< - Used in Kickoff (KDE 4.x.x) and Lancelot. Also used in MATE and Cinnamon (just FYI) - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[categories/32]
Size=32
Context=Categories
Type=Scalable
MinSize=32
MaxSize=256

########## Devices
########## ordered by size

#16x16 - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/16]
Size=16
Context=Devices
Type=Fixed


#16x16@2x - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/16@2x]
Size=16
Scale=2
Context=Devices
Type=Fixed

#16x16@3x - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/16@3x]
Size=16
Scale=3
Context=Devices
Type=Fixed

#22x22 - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/22]
Size=22
Context=Devices
Type=Fixed

#22x22@2x - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/22@2x]
Size=22
Scale=2
Context=Devices
Type=Fixed

#22x22@3x - Fixed size - For small device icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[devices/22@3x]
Size=22
Scale=3
Context=Devices
Type=Fixed

#64x64 - Scalable - For device icons >!!!ONLY!!!< - Scalable to the following sizes: 64x64 (default), 32x32, 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[devices/64]
Size=64
Context=Devices
Type=Scalable
MinSize=24
MaxSize=256

########## Emblems
########## ordered by size

#8x8 - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/8]
Size=8
Context=Emblems
Type=Fixed

#16x16 - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/16]
Size=16
Context=Emblems
Type=Fixed

#16x16@2x - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/16@2x]
Size=16
Scale=2
Context=Emblems
Type=Fixed

#16x16@3x - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/16@3x]
Size=16
Scale=3
Context=Emblems
Type=Fixed

#22x22 - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/22]
Size=22
Context=Emblems
Type=Fixed

#22x22@2x - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/22@2x]
Size=22
Scale=2
Context=Emblems
Type=Fixed

#22x22@3x - Fixed size - File system emblems - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[emblems/22@3x]
Size=22
Scale=3
Context=Emblems
Type=Fixed

########## Emoticons
########## ordered by size

#22x22 - Fixed size - Emoticons - DO_NOT_USE_ANYWHERE_ELSE - Color/flat
[emotes/22]
Size=22
Context=Emotes
Type=Fixed

#22x22@2x - Fixed size - Emoticons - DO_NOT_USE_ANYWHERE_ELSE - Color/flat
[emotes/22@2x]
Size=22
Scale=2
Context=Emotes
Type=Fixed

#22x22@3x - Fixed size - Emoticons - DO_NOT_USE_ANYWHERE_ELSE - Color/flat
[emotes/22@3x]
Size=22
Scale=3
Context=Emotes
Type=Fixed

########## Mimetypes
########## ordered by size

#16x16 - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/16]
Size=16
Context=MimeTypes
Type=Fixed
MinSize=16

#16x16@2x - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/16@2x]
Size=16
Scale=2
Context=MimeTypes
Type=Fixed
MinSize=16

#16x16@3x - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/16@3x]
Size=16
Scale=3
Context=MimeTypes
Type=Fixed
MinSize=16

#22x22 - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/22]
Size=22
Context=MimeTypes
Type=Scalable
MinSize=22
MaxSize=24

#22x22@2x - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/22@2x]
Size=22
Scale=2
Context=MimeTypes
Type=Scalable
MinSize=22
MaxSize=24

#22x22@3x - Fixed size - For small file type icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[mimetypes/22@3x]
Size=22
Scale=3
Context=MimeTypes
Type=Scalable
MinSize=22
MaxSize=24

#32x32 - Scalable - For file type icons >!!!ONLY!!!< - Scalable to the following sizes: 64x64 (default), 32x32, 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[mimetypes/32]
Size=32
Context=MimeTypes
Type=Fixed

#64x64 - Scalable - For file type icons >!!!ONLY!!!< - Scalable to the following sizes: 64x64 (default), 32x32, 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[mimetypes/64]
Size=64
Context=MimeTypes
Type=Scalable
MinSize=64
MaxSize=256

########## Places
########## ordered by size

#16x16 - Fixed size - For small folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[places/16]
Size=16
Context=Places
Type=Fixed
MinSize=16

#16x16@2x - Fixed size - For small folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[places/16@2x]
Size=16
Scale=2
Context=Places
Type=Fixed
MinSize=16

#16x16@3x - Fixed size - For small folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[places/16@3x]
Size=16
Scale=3
Context=Places
Type=Fixed
MinSize=16

#22x22 - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. KMail trash icon - WRONG_ICON_USAGE_BY_APP - Monochrome
[places/22]
Size=22
Context=Places
Type=Fixed

#22x22@2x - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. KMail trash icon - WRONG_ICON_USAGE_BY_APP - Monochrome
[places/22@2x]
Size=22
Scale=2
Context=Places
Type=Fixed

#22x22@3x - Fixed size - Workaround icon(s) for toolbar(s) button(s) e.g. KMail trash icon - WRONG_ICON_USAGE_BY_APP - Monochrome
[places/22@3x]
Size=22
Scale=3
Context=Places
Type=Fixed

#32x32 - Fixed size - For folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[places/32]
Size=32
Context=Places
Type=Fixed

#48x48 - Fixed size - For folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[places/48]
Size=48
Context=Places
Type=Fixed

#64x64 - Fixed size - For folder icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[places/64]
Size=64
Context=Places
Type=Fixed

#96x96 - Scalable - For folder icons >!!!ONLY!!!< - Scalable to the following sizes: 96x96 (default), 128x128, 256x256 - DO_NOT_USE_ANYWHERE_ELSE - Color
[places/96]
Size=96
Context=Places
Type=Scalable
MinSize=96
MaxSize=256

########## Status
########## ordered by size

#16x16 - Fixed size - For IM status icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/16]
Size=16
Context=Status
Type=Fixed

#16x16@2x - Fixed size - For IM status icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/16@2x]
Size=16
Scale=3
Context=Status
Type=Fixed

#16x16@3x - Fixed size - For IM status icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/16@3x]
Size=16
Scale=2
Context=Status
Type=Fixed

#22x22 - Fixed size - Icon(s) for Plasma theme/System Tray. Not particularly used on Plasma. - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/22]
Size=22
Context=Status
Type=Fixed

#22x22@2x - Fixed size - Icon(s) for Plasma theme/System Tray. Not particularly used on Plasma. - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/22@2x]
Size=22
Scale=2
Context=Status
Type=Fixed

#22x22@3x - Fixed size - Icon(s) for Plasma theme/System Tray. Not particularly used on Plasma. - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/22@3x]
Size=22
Scale=3
Context=Status
Type=Fixed

#24x24 - Fixed size - for GTK apps. - WRONG_ICON_USAGE_BY_APP - Monochrome
[status/24]
Size=24
Context=Status
Type=Fixed

#32x32 - Fixed size - Icon(s) for Plasma theme/System Tray. Not particularly used on Plasma. - DO_NOT_USE_ANYWHERE_ELSE - Monochrome
[status/32]
Size=32
Context=Status
Type=Fixed

#48x48 - Fixed size - For dialog icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[status/48]
Size=48
Context=Status
Type=Fixed

#64x64 - Fixed size - For dialog icons >!!!ONLY!!!< - DO_NOT_USE_ANYWHERE_ELSE - Color
[status/64]
Size=64
Context=Status
Type=Scalable
MinSize=22
MaxSize=256

# Gnome symbolic icons

[actions/symbolic]
Context=Actions
Size=16
MinSize=8
MaxSize=512
Type=Scalable

[devices/symbolic]
Context=Devices
Size=16
MinSize=8
MaxSize=512
Type=Scalable

[emblems/symbolic]
Context=Emblems
Size=16
MinSize=8
MaxSize=512
Type=Scalable

[places/symbolic]
Context=Places
Size=16
MinSize=8
MaxSize=512
Type=Scalable

[status/symbolic]
Context=Status
Size=16
MinSize=8
MaxSize=512
Type=Scalable

########## EOF
```
I'm not sure if I'm helping or hurting here :)

---

### Post by Perfect Storm on 2022-08-01
But... it shouldn't affect the way the icons is rendered...

---

### Post by #&amp;thj^% on 2022-08-01
I Fixed it :P
I changed only this in index:
```
# KDE Specific Stuff
DisplayDepth=32

Inherits=breeze,hicolor

Example=folder

FollowsColorScheme=true

DesktopDefault=48
DesktopSizes=16,22,32,48,64,128,256
ToolbarDefault=22
ToolbarSizes=16,22,32,48
MainToolbarDefault=22
MainToolbarSizes=16,22,32,48
SmallDefault=16
SmallSizes=16,22,32,48
PanelDefault=48
PanelSizes=16,22,32,48,64,128,256
DialogDefault=32
DialogSizes=16,22,32,48,64,128,256

KDE-Extensions=.svg
```

---

### Post by Perfect Storm on 2022-08-02
I can't see the difference :-k

---

### Post by #&amp;thj^% on 2022-08-02
I'll lend you my eye glasses then... :D
I neglected to show where some bad Icons were shown...but it's all good I've now cleaned up my system back to my preferred state.
They render better on XFCE4 though.

---

### Post by Perfect Storm on 2022-08-02
> **1fallen said:**
> I'll lend you my eye glasses then... :D
I neglected to show where some bad Icons were shown...but it's all good I've now cleaned up my system back to my preferred state.
They render better on XFCE4 though.

okay :D


You may like my new project though, it will come in different colors.

[IMG][[img]http://i.imgur.com/qZIgUYXh.png[/img]](https://imgur.com/qZIgUYX)[/IMG]

---

### Post by #&amp;thj^% on 2022-08-02
Oh Hell yes, that's right up my alley...:D where is Link??
verbiage Rated PG

---

### Post by Perfect Storm on 2022-08-02
> **1fallen said:**
> Oh Hell yes, that's right up my alley...:D where is Link??
verbiage Rated PG

It's not finished yet. This one takes time, but 2-4 weeks should be the timeline for its release.

---

### Post by #&amp;thj^% on 2022-08-02
> **Perfect Storm said:**
> It's not finished yet. This one takes time, but 2-4 weeks should be the timeline for its release.
I can't wait, >>> Are we there yet? Are we there yet? Are we there yet? 
That one I do want though in all seriousness.
Nice Work Perfect Storm

---

### Post by Perfect Storm on 2022-08-02
> **1fallen said:**
> I can't wait, >>> Are we there yet? Are we there yet? Are we there yet? 
That one I do want though in all seriousness.
Nice Work Perfect Storm

Thank you.

Now you've tried some of my icons. Are there any request for your apps you use? So I can fix it before I get the new icon sets released.

---

### Post by Perfect Storm on 2022-08-03
[[img]http://i.imgur.com/7P3JdQ7h.png[/img]](https://imgur.com/7P3JdQ7)

Now the apps and folder icons are made, then comes the tedious job with mimetype icons.

---

### Post by #&amp;thj^% on 2022-08-03
Looking Mighty Fine! but hurry will ya...:lolflag:
You know I'm joking

---

### Post by Perfect Storm on 2022-08-04
I may get it done  in this weekend. Depending how well the rest goes. Mimetypes are done. Now for devices which is the last category I'm missing. I'll release the blue version, one for light mode and one for dark mode and then later add other colors.

---

### Post by #&amp;thj^% on 2022-08-04
Perfect! ;)

---

### Post by Perfect Storm on 2022-08-07
Version 1.1 is out!

[LIST]
[*]Added: Protonmail, Mednaffe, Pulse effect
[*]Added: extra mime-type icons
[*]Games: (Steam) Banner of Ruin, (Steam) Paths & Danger,
[*]Games: (Steam) The Hands of Merlin, (Steam) KeeperRL,
[*]Changed: Pulse Audio control, Firmware, Gnome Photos,
[/LIST]

---

### Post by Perfect Storm on 2022-08-14
Version 1.2 is out!!!

[LIST]
[*]Added: Boinc, Rambox Pro, SteamLink, Plex,
[*]Added: Transmission Remote, Denemo, MS Edge,
[*]Added: seahorse, redshift,
[*]Added: extra mime-type icons
[*]Games: OpenMW
[*]Games: (Steam) Two Point Campus,
[*]Changed: Brasero, Keepass 1+2+x2+xc, xournal,
[*]Changed: Darktable, easyTAG, freeCAD, k3b,
[*]Changed: XFburn,
[/LIST]

---

### Post by Perfect Storm on 2022-11-04
Major update!

Version 2.0 is out!

[LIST]
[*]NEW: All Icon folders remade
[*]NEW: Better Ubuntu Budgie support
[*]Apps: htop, Istopo, QT V4L2 utility & test utility, Apport,
[*]Apps: Goodvibes, Budgie Screenshot, Fileroller, Font Manager,
[*]Apps: Gpodder, Budgie Preview, Budgie Shuffler, color manager,
[*]Games: (Steam) Graveyard Keeper, (Steam) Low Magic Age,
[*]Games: (Steam) Iratus - Lord of the Undead,
[/LIST]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291223&stc=1&d=1667604987[/IMG]

---

