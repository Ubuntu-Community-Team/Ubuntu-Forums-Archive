---
title: "OsSeC-hIdS won't extract~~~Lame...."
date: 2007-09-15
forum: Server Platforms
---

### Post by ATiwolf on 2007-09-15
I folowed the instructions from the manual and from a post in the forums detailing how to install ossec-hids...but when i get to the part where you select your language i get this:

atiwolf@atiwolf-Linux:~/ossec-hids-1.3$ ./install.sh

  ** Para instalação em português, escolha [br].
  ** &#35201;&#20351;&#29992;&#20013;&#25991;&#36827;&#34892;&#23433;&#35013;, &#35831;&#36873;&#25321; [cn].
  ** Fur eine deutsche Installation wohlen Sie [de].
  ** For installation in English, choose [en].
  ** Para instalar en Español , eliga [es].
  ** Pour une installation en français, choisissez [fr]
  ** Per l'installazione in Italiano, scegli [it].
  ** &#26085;&#26412;&#35486;&#12391;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12375;&#12414;&#12377;&#65294;&#36984;&#25246;&#12375;&#12390;&#19979;&#12373;&#12356;&#65294;[jp].
  ** Aby instalowa&#263; w j&#281;zyku Polskim, wybierz [pl].
  ** &#1044;&#1083;&#1103; &#1080;&#1085;&#1089;&#1090;&#1088;&#1091;&#1082;&#1094;&#1080;&#1081; &#1087;&#1086; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1077; &#1085;&#1072; &#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1084; ,&#1074;&#1074;&#1077;&#1076;&#1080;&#1090;&#1077; [ru].
  ** Za instalaciju na srpskom, izaberi [sr].
  ** Türkçe kurulum için seçin [tr].
  (en/br/cn/de/es/fr/it/jp/pl/ru/sr/tr) [en]: en

 Error 0x2.
 You must be root to use this script.

atiwolf@atiwolf-Linux:~/ossec-hids-1.3$

Why?
[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

### Post by wirelessmonkey on 2007-09-15
because something in the script requires root priveledges and you are not root....
try: sudo ./install.sh

---

### Post by ATiwolf on 2007-09-15
!-It works!thanks...wait...crap i have to install build essentials first...ill get back to you and let you know how things went down..
[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

### Post by ATiwolf on 2007-09-15
Alrighty everything works.Apreciate your help
[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

