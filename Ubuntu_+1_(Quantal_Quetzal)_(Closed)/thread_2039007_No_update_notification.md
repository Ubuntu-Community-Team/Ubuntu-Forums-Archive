---
title: "No update notification"
date: 2012-08-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Curtis6767 on 2012-08-07
I have not used sudo commands or the Software Updater to update Alpha 3 for the last week. I wanted to see if I would get an update notification. 

I last updated on Monday, July 30th. Since then I have purposely not used sudo commands nor have I clicked on Software Updater.

I do not have Synaptic installed and I have my Updates tab set up exactly as it is in 12.04.

I just am wondering why I'm not being notified of updates.

Thanks

---

### Post by ventrical on 2012-08-08
I just checked that out . Usually after a fresh install there seems to be a run-once type scenario. I just ran the software updater and there is an option <remind me later>. I clicked on that to see what will happen. I'll let you know , otherwise, later. Usually there is a notifications tool that can  turn it off and on.

---

### Post by philinux on 2012-08-14
This might be a bug. On 12.04 within about 10 mins of startup sometimes less update manager will get focus and minimise to the dash. It shows in the tile how many updates there are.

On 12.10 I've not had one auto launch of UM. This must be an update-notifer bug.

I've checked in startup apps and it's checkbox is ticked. Launching from terminal shows it's running. I have lots of updates pending if I manually check.

```
update-notifier

** (update-notifier:2434): WARNING **: already running?
```

So I killed the process. Launching from terminal produces all these errors. And there it hangs.

```
$ update-notifier
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
```

Any ideas before I bug report it.

---

### Post by dino99 on 2012-08-14
> **philinux said:**
> 
```
$ update-notifier
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-loma-synthetic.conf", line 12: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf", line 21: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
```

Any ideas before I bug report it.

There is a thread here about that already : delete .fonts.conf file and .fontconfig folder, then logout/in and the new path will be used instead (see fontconfig changelog, but this should have been cleaned on upgrade. Its clearly not the case, so need to report it)

---

### Post by philinux on 2012-08-14
Dino,

This was a clean install. I deleted .fontconfig as that was the only folder in my home. I'm getting less errors now but it still hangs.

```
update-notifier
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
```

---

### Post by GreatDanton on 2012-08-14
philinux try this: [http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)
or if you don't need fancy fonts you can also remove them.

---

### Post by grahammechanical on 2012-08-14
I do not know if this is helpful but, in Software Sources (in System Settings) and under the Updates tab there are some options:

Automatically check for updates - Daily, Every two days, Weekly, Every fortnight, Never

When there are security updates - Display immediately, Download automatically, Download and install automatically

When there are other updates - Display immediately, Display weekly, Display every two weeks

On my system I am set to have daily checks for updates but security updates displayed immediately and other software updates displayed weekly.

So, with those settings I do not expect to get any notification unless it is for a security update or it is more than a week since my last update.

I think that things are arranged this way so as not to frighten the horses with an unexpected update notification. I know that I used to jump when something flashed on the screen for a brief second and then minimized to the Launcher.

Regards

---

### Post by philinux on 2012-08-14
Ok first I did this.

sudo fc-cache -f -v which is why I reduced the errors. Then I renamed /etc/fonts/conf.d/90-fonts-nanum.conf to /etc/fonts/conf.d/90-fonts-nanum.conf.back and reran sudo fc-cache -f -v with no errors.

update-notifier now runs without errors.

[edit] I ran ubuntu-bug update-notifer and got a message about it's .desktop file being modified so i had a peek. What the heck is this.

 ```
cat /etc/xdg/autostart/update-notifier.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Update Notifier
Name[af]=Opdateringskennisgewing
Name[am]=&#4840;&#4635;&#4667;&#4667;&#4843; &#4768;&#4659;&#4659;&#4706;
Name[an]=Notificador d'esvielles
Name[ar]=&#1605;&#1588;&#1593;&#1585; &#1575;&#1604;&#1578;&#1581;&#1583;&#1610;&#1579;&#1575;&#1578;
Name[ast]=Notificador d'anovamientos
Name[be]=&#1055;&#1072;&#1074;&#1077;&#1076;&#1072;&#1084;&#1083;&#1103;&#1083;&#1100;&#1085;&#1110;&#1082; &#1072;&#1073;&#1085;&#1072;&#1118;&#1083;&#1077;&#1085;&#1100;&#1085;&#1103;&#1118;
Name[bg]=&#1048;&#1079;&#1074;&#1077;&#1089;&#1090;&#1103;&#1074;&#1072;&#1085;&#1077; &#1079;&#1072; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;
Name[bn]=&#2489;&#2494;&#2482;&#2472;&#2494;&#2455;&#2494;&#2470; &#2474;&#2480;&#2509;&#2479;&#2476;&#2503;&#2453;&#2509;&#2487;&#2453;
Name[br]=Meziant da gemenn an hizivadurioù
Name[bs]=Ukazivanje na nova unaprje&#273;enja
Name[ca]=Gestor d'actualitzacions
Name[ca@valencia]=Gestor d'actualitzacions
Name[cs]=Oznamování aktualizací
Name[csb]=Wiédzba ò aktualizacëjach
Name[da]=Opdateringspåmindelse
Name[de]=Aktualisierungsbenachrichtigung
Name[el]=&#917;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#949;&#957;&#951;&#956;&#949;&#961;&#974;&#963;&#949;&#969;&#957;
Name[en_AU]=Update Notifier
Name[en_CA]=Update Notifier
Name[en_GB]=Update Notifier
Name[eo]=Atentigilo pri &#285;isdatigoj
Name[es]=Notificador de actualizaciones
Name[et]=Uuendustest teataja
Name[eu]=Eguneratze berriemailea
Name[fi]=Päivitysilmoitin
Name[fo]=Frásøguforrit til dagføringar
Name[fr]=Notificateur de mises à jour
Name[fy]=Bywurkingmelder
Name[gd]=Cuir fios air ùrachadh
Name[gl]=Notificador de actualizacións
Name[he]=&#1502;&#1514;&#1512;&#1497;&#1506; &#1492;&#1506;&#1491;&#1499;&#1493;&#1504;&#1497;&#1501;
Name[hi]=&#2309;&#2342;&#2381;&#2351;&#2340;&#2344; &#2309;&#2343;&#2367;&#2360;&#2370;&#2330;&#2325;
Name[hr]=Update Notifier
Name[hu]=Frissítésfigyel&#337;
Name[id]=Pemberitahu Update
Name[is]=Tilkynningar um uppfærslur
Name[it]=Notifica aggiornamenti
Name[ja]=&#12450;&#12483;&#12503;&#12487;&#12540;&#12488;&#36890;&#30693;
Name[ka]=&#4306;&#4304;&#4316;&#4304;&#4334;&#4314;&#4308;&#4305;&#4308;&#4305;&#4312;&#4321; &#4315;&#4304;&#4330;&#4316;&#4308;
Name[kk]=&#1046;&#1072;&#1187;&#1072;&#1088;&#1090;&#1091;&#1083;&#1072;&#1088; &#1084;&#1241;&#1083;&#1110;&#1084;&#1076;&#1077;&#1084;&#1077;&#1083;&#1077;&#1088;&#1110;
Name[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6023;&#6076;&#6035;&#8203;&#6026;&#6086;&#6030;&#6073;&#6020;&#8203;&#6036;&#6021;&#6098;&#6021;&#6075;&#6036;&#6098;&#6036;&#6035;&#6098;&#6035;&#6039;&#6070;&#6038;
Name[ko]=&#50629;&#45936;&#51060;&#53944; &#50508;&#47532;&#48120;
Name[ku]=Hi&#351;yarkera Rojanekirinê
Name[lt]=Atnaujinim&#371; pranešiklis
Name[lv]=Atjaunin&#257;šanu atg&#257;din&#257;t&#257;js
Name[mn]=&#1064;&#1080;&#1085;&#1101;&#1095;&#1083;&#1101;&#1083; &#1084;&#1101;&#1076;&#1101;&#1101;&#1083;&#1101;&#1075;&#1095;
Name[mr]=&#2344;&#2369;&#2340;&#2344;&#2368;&#2325;&#2352;&#2339; &#2342;&#2352;&#2381;&#2358;&#2325;.
Name[ms]=Pemaklum Kemaskini
Name[my]=Update Notifier
Name[nb]=Oppdateringsvarsler
Name[nds]=Opfrischenhenwies
Name[nl]=Updatemelder
Name[nn]=Oppdateringsvarslar
Name[oc]=Notificador de mesas a jorn
Name[pa]=&#2565;&#2673;&#2602;&#2593;&#2631;&#2591; &#2616;&#2626;&#2586;&#2600;&#2622;
Name[pl]=Powiadamianie o aktualizacjach
Name[pt]=Notificador de Actualizações
Name[pt_BR]=Notificador de atualizações
Name[ro]=Notificare actualiz&#259;ri
Name[ru]=&#1054;&#1087;&#1086;&#1074;&#1077;&#1097;&#1077;&#1085;&#1080;&#1077; &#1086;&#1073; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;&#1093;
Name[si]=&#3514;&#3535;&#3520;&#3501;&#3530;&#3482;&#3535;&#3517;&#3538;&#3505; &#3505;&#3538;&#3520;&#3546;&#3503;&#3482;&#3514;
Name[sk]=Upozornenie na aktualizácie
Name[sl]=Obvestilnik o posodobitvah
Name[sq]=Njoftuesi i Rifreskimeve
Name[sr]=&#1054;&#1073;&#1072;&#1074;&#1077;&#1096;&#1090;&#1072;&#1074;&#1072;&#1095; &#1086;&#1089;&#1074;&#1077;&#1078;&#1077;&#1114;&#1072;
Name[sv]=Uppdateringsnotifierare
Name[ta]=&#2986;&#3009;&#2980;&#3009;&#2986;&#3021;&#2986;&#3007;&#2986;&#3021;&#2986;&#3009; &#2949;&#2993;&#3007;&#2997;&#3007;&#2986;&#3021;&#2986;&#3006;&#2995;&#2992;&#3021;
Name[te]=&#3112;&#3125;&#3136;&#3093;&#3120;&#3107;-&#3128;&#3138;&#3098;&#3135;&#3093;
Name[th]=&#3650;&#3611;&#3619;&#3649;&#3585;&#3619;&#3617;&#3649;&#3592;&#3657;&#3591;&#3648;&#3605;&#3639;&#3629;&#3609;&#3585;&#3634;&#3619;&#3611;&#3619;&#3633;&#3610;&#3611;&#3619;&#3640;&#3591;
Name[tr]=Güncelle&#351;tirme Bildiricisi
Name[ug]=&#1610;&#1744;&#1709;&#1609;&#1604;&#1575;&#1588; &#1582;&#1749;&#1739;&#1749;&#1585;&#1670;&#1609;&#1587;&#1609;
Name[uk]=&#1057;&#1087;&#1086;&#1074;&#1110;&#1097;&#1077;&#1085;&#1085;&#1103; &#1087;&#1088;&#1086; &#1086;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1103;
Name[vi]=Trình Nh&#7855;c nh&#7903; c&#7853;p nh&#7853;t
Name[zh_CN]=&#26356;&#26032;&#25552;&#31034;
Name[zh_HK]=&#26356;&#26032;&#36890;&#30693;&#31243;&#24335;
Name[zh_TW]=&#26356;&#26032;&#36890;&#21578;
Comment=Check for available updates automatically
Comment[af]=Kontroleer automaties vir nuwe opdaterings
Comment[an]=Comprebar automaticament os esvielles disponibles
Comment[ar]=&#1575;&#1604;&#1578;&#1605;&#1587; &#1575;&#1604;&#1578;&#1581;&#1583;&#1610;&#1579;&#1575;&#1578; &#1578;&#1604;&#1602;&#1575;&#1574;&#1610;&#1575;
Comment[ast]=Comprobar automáticamente los anovamientos disponibles
Comment[be]=&#1055;&#1088;&#1072;&#1074;&#1103;&#1088;&#1072;&#1094;&#1100; &#1085;&#1072; &#1076;&#1072;&#1089;&#1090;&#1091;&#1087;&#1085;&#1072;&#1089;&#1100;&#1094;&#1100; &#1072;&#1073;&#1085;&#1072;&#1118;&#1083;&#1077;&#1085;&#1100;&#1085;&#1103;&#1118; &#1072;&#1118;&#1090;&#1072;&#1084;&#1072;&#1090;&#1099;&#1095;&#1085;&#1072;
Comment[bg]=&#1040;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1085;&#1072; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1082;&#1072; &#1079;&#1072; &#1085;&#1072;&#1083;&#1080;&#1095;&#1085;&#1080; &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080;
Comment[bn]=&#2488;&#2509;&#2476;&#2527;&#2434;&#2453;&#2509;&#2480;&#2495;&#2527;&#2477;&#2494;&#2476;&#2503; &#2472;&#2468;&#2497;&#2472; &#2489;&#2494;&#2482;&#2472;&#2494;&#2455;&#2494;&#2470;&#2503;&#2480; &#2460;&#2472;&#2509;&#2479; &#2454;&#2507;&#2433;&#2460; &#2453;&#2480;&#2494; &#2489;&#2476;&#2503;
Comment[br]=Gwiriañ hizivadurioù hegerz emgefre
Comment[bs]=Automatski provjeriti da li ima dostupnih unaprje&#273;enja
Comment[ca]=Comprova si hi ha actualizacions disponibles automàticament.
Comment[ca@valencia]=Comprova si hi ha actualizacions disponibles automàticament.
Comment[cs]=Automaticky kontrolovat dostupné aktualizace
Comment[csb]=Aùtomatné sprôwdzanié przëstãpnotë aktualizacëjów
Comment[da]=Kontrollér automatisk for tilgængelige opdateringer
Comment[de]=Automatisch nach verfügbaren Aktualisierungen suchen
Comment[el]=&#913;&#965;&#964;&#972;&#956;&#945;&#964;&#959;&#962; &#941;&#955;&#949;&#947;&#967;&#959;&#962; &#947;&#953;&#945; &#949;&#957;&#951;&#956;&#949;&#961;&#974;&#963;&#949;&#953;&#962;
Comment[en_AU]=Check for available updates automatically
Comment[en_CA]=Check for available updates automatically
Comment[en_GB]=Check for available updates automatically
Comment[eo]=A&#365;tomate kontroli pri disponeblaj &#285;isdatigoj
Comment[es]=Comprobar automáticamente las actualizaciones disponibles
Comment[et]=Olemasolevate uuenduste automaatne kontroll
Comment[eu]=Automatikoki bilatu eguneraketa berriak
Comment[fi]=Tarkista saatavilla olevat päivitykset automaattisesti
Comment[fo]=Kanna sjálvvirkandi eftir tøkum dagførslum
Comment[fr]=Vérifier automatiquement la disponibilité de mises à jour
Comment[gd]=Sgrùd son ùrachadh fèin-obrachail ri làimh
Comment[gl]=Comprobar automaticamente as actualizacións dispoñíbeis
Comment[he]=&#1489;&#1491;&#1497;&#1511;&#1492; &#1488;&#1493;&#1496;&#1493;&#1502;&#1496;&#1497;&#1514; &#1488;&#1495;&#1512; &#1506;&#1491;&#1499;&#1493;&#1504;&#1497;&#1501;
Comment[hi]=&#2360;&#2381;&#2357;&#2340;&#2307; &#2309;&#2342;&#2381;&#2351;&#2340;&#2344; &#2313;&#2346;&#2354;&#2348;&#2381;&#2343;&#2340;&#2366; &#2361;&#2375;&#2340;&#2369; &#2332;&#2366;&#2305;&#2330;
Comment[hr]=Automatski provjeri za dostupne nadogradnje
Comment[hu]=Frissítések keresése automatikusan
Comment[id]=Periksa keberadaan pembaruan secara otomatis
Comment[is]=Leita að uppfærslum sjálfkrafa
Comment[it]=Controlla automaticamente la disponibilità di aggiornamenti
Comment[ja]=&#21033;&#29992;&#21487;&#33021;&#12394;&#12450;&#12483;&#12503;&#12487;&#12540;&#12488;&#12434;&#33258;&#21205;&#30340;&#12395;&#12481;&#12455;&#12483;&#12463;&#12377;&#12427;
Comment[ka]=&#4306;&#4304;&#4316;&#4304;&#4334;&#4314;&#4308;&#4305;&#4308;&#4305;&#4310;&#4308; &#4304;&#4309;&#4322;&#4317;&#4315;&#4304;&#4322;&#4323;&#4320;&#4312; &#4328;&#4308;&#4315;&#4317;&#4332;&#4315;&#4308;&#4305;&#4304;
Comment[kk]=&#1046;&#1072;&#1187;&#1072;&#1088;&#1090;&#1091;&#1083;&#1072;&#1088;&#1076;&#1099;&#1187; &#1078;&#1077;&#1090;&#1110;&#1084;&#1076;&#1110;&#1075;&#1110;&#1085; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1090;&#1099; &#1090;&#1199;&#1088;&#1076;&#1077; &#1090;&#1077;&#1082;&#1089;&#1077;&#1088;&#1091;
Comment[km]=&#6038;&#6071;&#6035;&#6071;&#6031;&#6098;&#6041;&#8203;&#6040;&#6078;&#6043;&#8203;&#6036;&#6021;&#6098;&#6021;&#6075;&#6036;&#6098;&#6036;&#6035;&#6098;&#6035;&#6039;&#6070;&#6038;&#8203;&#6026;&#6082;&#6043;&#8203;&#6040;&#6070;&#6035;&#8203;&#6026;&#6084;&#6041;&#8203;&#6047;&#6098;&#6044;&#6096;&#6041;&#8203;&#6036;&#6098;&#6042;&#6044;&#6031;&#6098;&#6031;&#6071;
Comment[ko]=&#51088;&#46041;&#51004;&#47196; &#49324;&#50857;&#54624; &#49688; &#51080;&#45716; &#50629;&#45936;&#51060;&#53944; &#54869;&#51064;
Comment[ku]=Bixweber li rojanekirinên amade bigere
Comment[lt]=Ieškoti prieinam&#371; atnaujinim&#371; automatiškai
Comment[lv]=Autom&#257;tiski p&#257;rbaud&#299;t pieejamos jaunin&#257;jumus
Comment[mn]=&#1048;&#1076;&#1101;&#1074;&#1093;&#1080;&#1090;&#1101;&#1081; &#1096;&#1080;&#1085;&#1101;&#1095;&#1083;&#1101;&#1083;&#1080;&#1081;&#1075; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1072;&#1072;&#1088; &#1096;&#1072;&#1083;&#1075;&#1072;&#1093;
Comment[mr]=&#2313;&#2346;&#2354;&#2348;&#2381;&#2343; &#2309;&#2346;&#2337;&#2375;&#2335;&#2381;&#2360; &#2310;&#2346;&#2379;&#2310;&#2346; &#2358;&#2379;&#2343;&#2366;.
Comment[ms]=Periksa kemaskini yang sedia ada secara automatik.
Comment[my]=&#4123;&#4123;&#4158;&#4141;&#4116;&#4141;&#4143;&#4100;&#4154;&#4126;&#4145;&#4140; Updates &#4121;&#4155;&#4140;&#4152;&#4096;&#4141;&#4143;&#4129;&#4124;&#4141;&#4143;&#4129;&#4124;&#4155;&#4145;&#4140;&#4096;&#4154;&#4101;&#4101;&#4154;&#4102;&#4145;&#4152;&#4121;&#4106;&#4154;&#4171;
Comment[nb]=Se etter tilgjengelige oppdateringer automatisk
Comment[nds]=Nah verfögbaren Opfrischen vun alleen söken
Comment[nl]=Automatisch op updates controleren
Comment[nn]=Sjå etter tilgjengelege oppdateringar automatisk
Comment[oc]=Verificar automaticament la disponibilitat de mesas a jorn
Comment[pa]=&#2569;&#2602;&#2610;&#2673;&#2604;&#2599; &#2565;&#2673;&#2602;&#2593;&#2631;&#2591; &#2610;&#2568; &#2566;&#2591;&#2635;&#2606;&#2632;&#2591;&#2623;&#2581; &#2617;&#2624; &#2586;&#2632;&#2673;&#2581; &#2581;&#2608;&#2635;
Comment[pl]=Automatyczne sprawdzanie dost&#281;pno&#347;ci aktualizacji
Comment[pt]=Verificar actualizações disponíveis automaticamente
Comment[pt_BR]=Verificar automaticamente se há atualizações disponíveis
Comment[ro]=Verific&#259; automat actualiz&#259;rile disponibile
Comment[ru]=&#1040;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1103;&#1090;&#1100; &#1085;&#1072;&#1083;&#1080;&#1095;&#1080;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1081;
Comment[sd]=&#1583;&#1587;&#1578;&#1610;&#1575;&#1576; &#1578;&#1575;&#1586;&#1711;&#1610;&#1608;&#1606; &#1662;&#1575;&#1723;&#1605;&#1585;&#1575;&#1583;&#1608; &#1670;&#1706;&#1575;&#1587;&#1580;&#1606;
Comment[si]=&#3517;&#3510;&#3535; &#3484;&#3501; &#3524;&#3536;&#3482;&#3538; &#3514;&#3535;&#3520;&#3501;&#3530;&#3482;&#3535;&#3517;&#3538;&#3505; &#3523;&#3507;&#3524;&#3535; &#3523;&#3530;&#3520;&#3514;&#3458;&#3482;&#3530;*&#3515;&#3539;&#3514;&#3520; &#3508;&#3515;&#3538;&#3482;&#3530;&#3522;&#3535; &#3482;&#3515;&#3505;&#3530;&#3505;
Comment[sk]=Automaticky kontrolova&#357; dostupné aktualizácie
Comment[sl]=Samodejno preveri za posodobitve
Comment[sq]=Kontrollo automatikisht për përditësimet e disponueshme
Comment[sr]=&#1040;&#1091;&#1090;&#1086;&#1084;&#1072;&#1090;&#1089;&#1082;&#1080; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1080; &#1076;&#1072; &#1083;&#1080; &#1080;&#1084;&#1072; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1080;&#1093; &#1086;&#1089;&#1074;&#1077;&#1078;&#1077;&#1114;&#1072;
Comment[sv]=Leta automatiskt efter tillgängliga uppdateringar
Comment[te]=&#3077;&#3074;&#3110;&#3137;&#3116;&#3134;&#3103;&#3137;&#3122;&#3147;&#3112;&#3137;&#3112;&#3149;&#3112; &#3112;&#3125;&#3136;&#3093;&#3120;&#3107;&#3122;&#3112;&#3137; &#3128;&#3149;&#3125;&#3119;&#3074;&#3098;&#3134;&#3122;&#3093;&#3074;&#3095;&#3134; &#3114;&#3149;&#3120;&#3119;&#3108;&#3149;&#3112;&#3135;&#3074;&#3098;&#3137;
Comment[th]=&#3605;&#3619;&#3623;&#3592;&#3626;&#3629;&#3610;&#3585;&#3634;&#3619;&#3611;&#3619;&#3633;&#3610;&#3611;&#3619;&#3640;&#3591;&#3607;&#3637;&#3656;&#3652;&#3604;&#3657;&#3619;&#3633;&#3610;&#3585;&#3634;&#3619;&#3629;&#3609;&#3640;&#3597;&#3634;&#3605;&#3650;&#3604;&#3618;&#3629;&#3633;&#3605;&#3650;&#3609;&#3617;&#3633;&#3605;&#3636;
Comment[tr]=Güncelle&#351;tirmeleri otomatik olarak denetle
Comment[ug]=&#1610;&#1744;&#1709;&#1609;&#1604;&#1575;&#1606;&#1605;&#1609;&#1604;&#1575;&#1585;&#1606;&#1609;&#1709; &#1576;&#1575;&#1585; &#1610;&#1608;&#1602;&#1604;&#1735;&#1602;&#1609;&#1606;&#1609; &#1574;&#1575;&#1662;&#1578;&#1608;&#1605;&#1575;&#1578;&#1609;&#1603; &#1578;&#1749;&#1603;&#1588;&#1736;&#1585;&#1587;&#1735;&#1606;
Comment[uk]=&#1040;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1085;&#1086; &#1087;&#1077;&#1088;&#1077;&#1074;&#1110;&#1088;&#1103;&#1090;&#1080; &#1085;&#1072;&#1103;&#1074;&#1085;&#1110;&#1089;&#1090;&#1100; &#1086;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1100;
Comment[vi]=T&#7921; &#273;&#7897;ng ki&#7875;m tra v&#7873; các b&#7843;n c&#7853;p nh&#7853;t &#273;ang có
Comment[zh_CN]=&#33258;&#21160;&#26816;&#27979;&#21487;&#29992;&#30340;&#26356;&#26032;
Comment[zh_HK]=&#33258;&#21205;&#27298;&#26597;&#21487;&#29992;&#30340;&#26356;&#26032;
Comment[zh_TW]=&#33258;&#21205;&#27298;&#26597;&#26356;&#26032;
Icon=update-notifier
Exec=update-notifier
Terminal=false
Type=Application
Categories=
NotShowIn=KDE;
NoDisplay=false
X-GNOME-Autostart-Delay=60
X-Ubuntu-Gettext-Domain=update-notifier
```

---

### Post by philinux on 2012-08-14
I've restored the .fontconfig file since sudo fc-cache -f -v cleaned it up.

Bug report.

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1036634](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1036634)

---

