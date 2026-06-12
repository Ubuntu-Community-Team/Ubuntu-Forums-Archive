---
title: "Nautilus function &quot;Open with&quot; removed?"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by Abandon on 2013-04-05
I would like to use the function "open with" in Nautilus. This was default with earlier releases so you could open a VIDEO_TS map with VLC. I don't seem to find this feature within 13.04. Is there a dconf setting, a plugin or has it been removed?

---

### Post by dino99 on 2013-04-05
that option is still there; maybe you need to check if all the default packages are installed (ubuntu-desktop, or else), then run:

sudo dpkg-reconfigure -phigh -a
( be patient, it can take a while to endup itself)

---

### Post by Abandon on 2013-04-05
Just did a fresh install of 13.04 beta 2 and the option is not available. Ubuntu-desktop is installed and sudo dpkg-reconfigure -phigh -a didn't do the trick.

---

### Post by Harry33 on 2013-04-05
> **Abandon said:**
> I would like to use the function "open with" in Nautilus. This was default with earlier releases so you could open a VIDEO_TS map with VLC. I don't seem to find this feature within 13.04. Is there a dconf setting, a plugin or has it been removed?

Works here fine.
You mean you cannot do this:
Find (with nautilus) the appropriate file you want to open.
Then right-mouse click the file and choose the option "open with".

---

### Post by Abandon on 2013-04-05
No..that works indeed. I however would like to have this function with a map instead of a file. That was common with former editions of Ubuntu. The reason why is because I have several dvd's stored on my computer. If you can select a map (within this map you have VIDEO_TS) you can choose to open this map with another appllication like totem or VLC.

---

### Post by jbicha on 2013-04-05
I'm guessing by "map" you mean "folder" and yes Nautilus 3.6+ does not include "Open With" for folders. If you just want to open videos with VLC, have you tried System Settings>Details>Default Applications ?

---

### Post by mc4man on 2013-04-05
> **Abandon said:**
> I would like to use the function "open with" in Nautilus. This was default with earlier releases so you could open a VIDEO_TS map with VLC. I don't seem to find this feature within 13.04. Is there a dconf setting, a plugin or has it been removed?

It was removed in nautilus starting with 3.6 & declined to be restored in Ubuntu packages, a rather short-sighted decision but one nonetheless.
(at times I've found *some* VIDEO_TS folders are better opened from vlc as a dvd disc thru the browse option, that ensures proper dvd nav.

If you truly find useful (i do), then easily restored thru simple patch & build of nautilus, whether 3.6 or 3.8

---

### Post by Abandon on 2013-04-07
> **mc4man said:**
> It was removed in nautilus starting with 3.6 & declined to be restored in Ubuntu packages, a rather short-sighted decision but one nonetheless.
(at times I've found *some* VIDEO_TS folders are better opened from vlc as a dvd disc thru the browse option, that ensures proper dvd nav.

If you truly find useful (i do), then easily restored thru simple patch & build of nautilus, whether 3.6 or 3.8

A simple patch & build sounds good but I don't know how to do that I'm afraid.

---

### Post by rrnbtter on 2013-04-07
Greetings,
paste the following command into a termial and post the results. 

find /usr/share/applications -name 'vlc.desktop'

---

### Post by Abandon on 2013-04-08
The answer is no suprise  I think ;-) : /usr/share/applications/vlc.desktop

---

### Post by rrnbtter on 2013-04-08
Greetings,

> **Abandon said:**
> The answer is no suprise  I think ;-) : /usr/share/applications/vlc.desktop

open the file with gedit and see if it looks like this. The part in bold is especially important because the %U allows the link to show under "open with".
Let me know what you find.
Also, sorry to take time to get back, I have odd work hours but after tonight I will be off for three days. 


[Desktop Entry]
Version=1.0
Name=VLC media player
GenericName=Media player
Comment=Read, capture, broadcast your multimedia streams
**Exec=/usr/bin/vlc %U**
TryExec=/usr/bin/vlc
Icon=vlc
Terminal=false
Type=Application
Categories=AudioVideo;Player;Recorder;
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;audio/amr;audio/amr-wb;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;application/xspf+xml;x-scheme-handler/mms;x-scheme-handler/rtmp;x-scheme-handler/rtsp;
X-KDE-Protocols=ftp,http,https,mms,rtmp,rtsp,sftp,smb
Keywords=Player;Capture;DVD;Audio;Video;Server;Broadcast;
Name[en_US]=vlc.desktop

---

### Post by Abandon on 2013-04-08
Ok..let me first thank you for all the work you are trying to do. My copy of Ubuntu 13.04 is still working within a virtualbox environment (on a Ubuntu 12.04 host). I made a mistake by telling you that the output of the command you asked me to do was /usr/share/applications/vlc.desktop It was so with 12.04 but not (!) from 13.04. Nothing happened, the output of that command is zip as in nothing. Strange because if I use cat /usr/share/applications/vlc.desktop I can see the following content, but the mentioned** Exec=/usr/bin/vlc %U** is also there.


[Desktop Entry]
Version=1.0
Name=VLC media player
GenericName=Media player
Comment=Read, capture, broadcast your multimedia streams
Name[bn]=VLC &#2478;&#2495;&#2465;&#2495;&#2479;&#2492;&#2494; &#2474;&#2509;&#2482;&#2503;&#2479;&#2492;&#2494;&#2480;
Comment[bn]=&#2438;&#2474;&#2472;&#2494;&#2480; &#2478;&#2494;&#2482;&#2509;&#2463;&#2495;&#2478;&#2495;&#2465;&#2495;&#2479;&#2492;&#2494; &#2488;&#2509;&#2463;&#2509;&#2480;&#2496;&#2478; &#2474;&#2465;&#2492;&#2497;&#2472;, &#2471;&#2480;&#2503; &#2480;&#2494;&#2454;&#2497;&#2472; &#2447;&#2476;&#2434; &#2459;&#2465;&#2492;&#2495;&#2479;&#2492;&#2503; &#2470;&#2495;&#2472;
Name[br]=VLC lenner mediaoù
GenericName[br]=Lenner mediaoù
Comment[br]=Lenn, enrollañ, skignañ ho lanvioù liesvedia
Name[ca]=Reproductor multimèdia VLC
GenericName[ca]=Reproductor multimèdia
Comment[ca]=Reproduïu, captureu i difoneu fluxos multimèdia
Name[de]=VLC Media Player
GenericName[de]=Medienwiedergabe
Comment[de]=Wiedergabe, Aufnahme und Verbreitung Ihrer Multimedia-Streams
Name[es]=Reproductor multimedia VLC
GenericName[es]=Reproductor multimedia
Comment[es]=Lea, capture y emita sus contenidos multimedia
Name[et]=VLC meediaesitaja
GenericName[et]=Meediaesitaja
Comment[et]=Multimeediafailide taasesitamine, lindistamine ja edastamine
Name[eu]=VLC multimedia irakurgailua
GenericName[eu]=Multimedia irakurgailua
Comment[eu]=Irakurri, hartu, igorri zure multimedia jarioak
Name[fi]=VLC-mediasoitin
GenericName[fi]=Mediasoitin
Comment[fi]=Toista, tallenna ja lähetä multimediaa
Name[fr]=Lecteur multimédia VLC
GenericName[fr]=Lecteur multimédia
Comment[fr]=Lire, capturer, diffuser vos flux multimedia
Name[gl]=Reprodutor multimedia VLC
GenericName[gl]=Reprodutor multimedia
Comment[gl]=Lea, capture e emita os seus fluxos multimedia
Name[he]=&#1504;&#1490;&#1503; &#1492;&#1502;&#1491;&#1497;&#1492; VLC
GenericName[he]=&#1504;&#1490;&#1503; &#1502;&#1491;&#1497;&#1492;
Comment[he]=&#1511;&#1512;&#1497;&#1488;&#1492;, &#1500;&#1499;&#1497;&#1491;&#1492; &#1493;&#1513;&#1497;&#1491;&#1493;&#1512; &#1513;&#1500; &#1514;&#1494;&#1512;&#1497;&#1502;&#1497; &#1502;&#1493;&#1500;&#1496;&#1497;&#1502;&#1491;&#1497;&#1492;
Name[hr]=Izvo&#273;a&#269; medija VLC                                                     
GenericName[hr]=Izvedba medija                                                  
Comment[hr]=Izvedba, snimanje i širenje Vaših multimedijalnih strujanja
Name[hu]=VLC médialejátszó
GenericName[hu]=Médialejátszó
Comment[hu]=Multimédiás adatfolyamok olvasása, mentése, szórása
Name[is]=VLC margmiðlunarspilarinn
GenericName[is]=Margmiðlunarspilari
Comment[is]=Spilar margmiðlunarefni ásamt því að taka upp og útvarpa straumum
Name[it]=Lettore multimediale VLC
GenericName[it]=Lettore multimediale
Comment[it]=Legge, acquisisce e trasmette i tuoi flussi multimediali
Name[ja]=VLC&#12513;&#12487;&#12451;&#12450;&#12503;&#12524;&#12452;&#12516;&#12540;
Comment[ja]=&#12510;&#12523;&#12481;&#12513;&#12487;&#12451;&#12450;&#12473;&#12488;&#12522;&#12540;&#12512;&#12398;&#35501;&#12415;&#36796;&#12415;&#12289;&#12461;&#12515;&#12503;&#12481;&#12515;&#12540;&#12289;&#12502;&#12525;&#12540;&#12489;&#12461;&#12515;&#12473;&#12488;
Name[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6021;&#6070;&#6016;&#6091;&#8203;&#6040;&#6081;&#6028;&#6080; VLC
Comment[km]=&#6050;&#6070;&#6035; &#6021;&#6070;&#6036;&#6091;&#6041;&#6016; &#6036;&#6098;&#6042;&#6016;&#6070;&#6047;&#8203;&#6047;&#6098;&#6033;&#6098;&#6042;&#6072;&#6040;&#8203;&#6038;&#6048;&#6075;&#6040;&#6081;&#6028;&#6080;&#8203;&#6042;&#6036;&#6047;&#6091;&#8203;&#6050;&#6098;&#6035;&#6016;
Name[lt]=VLC leistuv&#279; 
GenericName[lt]=Leistuv&#279;
Comment[lt]=Groti, &#303;rašyti, si&#371;sti &#303;vairialyp&#279;s terp&#279;s k&#363;rinius
Name[nl]=VLC Media Player
GenericName[nl]=Mediaspeler
Comment[nl]=Uw multimediastreams afspelen, opnemen en uitzenden
Name[nn]=VLC mediespelar
GenericName[nn]=Mediespelar
Comment[nn]=Spel av, ta opp og send ut multimedia
Name[pa]=VLC &#2606;&#2624;&#2593;&#2623;&#2566; &#2602;&#2610;&#2631;&#2565;&#2608;
Comment[pa]=&#2566;&#2602;&#2595;&#2624; &#2606;&#2610;&#2591;&#2624;&#2606;&#2624;&#2593;&#2623;&#2566; &#2616;&#2591;&#2608;&#2624;&#2606; &#2602;&#2652;&#2637;&#2617;&#2635;, &#2581;&#2632;&#2602;&#2586;&#2608; &#2596;&#2631; &#2604;&#2608;&#2622;&#2593;&#2581;&#2622;&#2616;&#2591; &#2581;&#2608;&#2635; 
Name[pl]=VLC media player
GenericName[pl]=Odtwarzacz multimedialny
Comment[pl]=Odczytywanie, przechwytywanie i nadawanie strumieni multimedialnych
Name[pt_BR]=Reprodutor de Mídias VLC
GenericName[pt_BR]=Reprodutor de Mídias
Comment[pt_BR]=Reproduza, capture e transmita os seus fluxos multimídia
Name[ru]=&#1052;&#1077;&#1076;&#1080;&#1072;&#1087;&#1083;&#1077;&#1077;&#1088; VLC
GenericName[ru]=&#1052;&#1077;&#1076;&#1080;&#1072;&#1087;&#1083;&#1077;&#1077;&#1088;
Comment[ru]=&#1059;&#1085;&#1080;&#1074;&#1077;&#1088;&#1089;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1087;&#1088;&#1086;&#1080;&#1075;&#1088;&#1099;&#1074;&#1072;&#1090;&#1077;&#1083;&#1100; &#1074;&#1080;&#1076;&#1077;&#1086; &#1080; &#1072;&#1091;&#1076;&#1080;&#1086;
Name[sk]=VLC media player
Comment[sk]=Naèítavajte, zaznamenávajte, vysielajte svoje multimediálne streamy
Name[sv]=Mediaspelaren VLC
GenericName[sv]=Mediaspelaren
Comment[sv]=Allmän uppspelare av film och musik
Name[te]=VLC &#3118;&#3134;&#3111;&#3149;&#3119;&#3118; &#3114;&#3149;&#3120;&#3110;&#3120;&#3149;&#3126;&#3093;&#3074;
GenericName[te]=&#3118;&#3134;&#3111;&#3149;&#3119;&#3118; &#3114;&#3149;&#3120;&#3110;&#3120;&#3149;&#3126;&#3093;&#3074;
Comment[te]=&#3118;&#3136; &#3116;&#3129;&#3137;&#3123;&#3118;&#3134;&#3111;&#3149;&#3119;&#3118; &#3114;&#3149;&#3120;&#3125;&#3134;&#3129;&#3134;&#3122;&#3112;&#3137; &#3098;&#3110;&#3137;&#3125;&#3137;, &#3116;&#3074;&#3111;&#3135;&#3074;&#3098;&#3137; &#3118;&#3120;&#3135;&#3119;&#3137; &#3114;&#3149;&#3120;&#3128;&#3134;&#3120;&#3074; &#3098;&#3143;&#3119;&#3135;
Name[uk]=&#1052;&#1077;&#1076;&#1110;&#1072;&#1087;&#1083;&#1077;&#1108;&#1088; VLC
GenericName[uk]=&#1052;&#1077;&#1076;&#1110;&#1072;&#1087;&#1083;&#1077;&#1108;&#1088;
Comment[uk]=&#1059;&#1085;&#1110;&#1074;&#1077;&#1088;&#1089;&#1072;&#1083;&#1100;&#1085;&#1080;&#1081; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1074;&#1072;&#1095; &#1074;&#1110;&#1076;&#1077;&#1086; &#1081; &#1072;&#1091;&#1076;&#1110;&#1086;
Name[wa]=Djouweu d' media VLC
GenericName[wa]=Djouweu d' media
Comment[wa]=Lét, egaloye, evoye vos floûs multimedia
Name[zh_CN]=VLC media player
GenericName[zh_CN]=&#23186;&#20307;&#25773;&#25918;&#22120;
Comment[zh_CN]=&#20026;&#24744;&#35835;&#21462;&#12289;&#25429;&#33719;&#25110;&#21457;&#36865;&#22810;&#23186;&#20307;&#27969;
Name[zh_TW]=VLC &#23186;&#39636;&#25773;&#25918;&#22120;
GenericName[zh_TW]=&#23186;&#39636;&#25773;&#25918;&#22120;
Comment[zh_TW]=&#35712;&#21462;&#12289;&#25847;&#21462;&#12289;&#24291;&#25773;&#24744;&#30340;&#22810;&#23186;&#39636;&#20018;&#27969;
Exec=/usr/bin/vlc %U
TryExec=/usr/bin/vlc
Icon=vlc
Terminal=false
Type=Application
Categories=AudioVideo;Player;Recorder;
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;audio/amr;audio/amr-wb;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;application/xspf+xml;x-scheme-handler/mms;x-scheme-handler/rtmp;x-scheme-handler/rtsp;
X-KDE-Protocols=ftp,http,https,mms,rtmp,rtsp,sftp,smb
Keywords=Player;Capture;DVD;Audio;Video;Server;Broadcast;

---

### Post by rrnbtter on 2013-04-08
Greetings,
Your file looks good to me. You should be able to open Nautilus and browse to /usr/share/applications and you should see a VLC Media Player. Based on what you have posted and if the file exists in that location you should have and "open with" option under the "right click" on on a media file in Nautilus.

---

### Post by Abandon on 2013-04-08
No, Nautilus has changed as of Gnome 3.6 and the feature you are refering to is gone. In Ubuntu 12.10 there was an older version of Nautilus but the 3.6 version of 13.04 is realy different then before. Typical Gnome...they are always making a bare bone system. And for who?

---

### Post by mc4man on 2013-04-08
> **Abandon said:**
> A simple patch & build sounds good but I don't know how to do that I'm afraid.

I'm a bit pressed for time till the weekend so can't really give you a decent walkthru to do a good build & install. 
Myself prefer to package build nautilus source in to the 6 packages, then replace the ones installed, usually 5 here, you likely would only need 3 of the 6.
Also it's possible nautilus will update again before release so you'd have to do again, a good reason to have a decent understanding, ect.

**IF** you wish now I'll give you something quick & easy, will take care of all changes for you & give you a slightly higher nautilus version but allow you to be notified if nautilus updates. (at which point we can re-address more verbosely, you don't have to update till ready to redo on your own  with patch.

So if inclined now instead of  just a patch we'll use a debdiff, this is good as written just for the current **1:3.6.3-0ubuntu14 source only**

in terminal - 
```
mkdir nautilus_build && cd nautilus_build
```
```
sudo apt-get build-dep nautilus
```
```
apt-get source nautilus && cd nautilus-3.6.3
```

**Leave the terminal open**, download attached, **extract **the debdiff & place in nautilus_build folder as in screen 1
Back at terminal - 
```
 *removed*, use one in post 26
```

You should see this - 
> ~/nautilus_build/nautilus-3.6.3$  patch -Np1 -i ../nautilus_3.6.3-0ubuntu14.1.debdiff
patching file debian/changelog
patching file debian/patches/open_with.patch
patching file debian/patches/series


If so then build packages
```
dpkg-buildpackage -rfakeroot -D -us -uc
```

When done  - 
```
cd .. && mkdir in && cd in
```
should look like in screen 2. **Leave the terminal open at "in" prompt** &  move all the  nautius source packages **you currently  have installed** into the 'in' folder, probably only 3 - 
libnautilus-extension1a_3.6.3-0ubuntu14.1
nautilus-data_3.6.3-0ubuntu14.1_all.deb
nautilus_3.6.3-0ubuntu14.1

The libnautilus-extension-dev & gir1.2-nautilus-3.0_3.6.3-0ubuntu14.1 packages are only needed if you are building other sources that depend on them, if you have them installed then also move into the "in" folder , the nautilus-dbg package you don't need at all. Screen 3 show in folder with the 3 min packages inside.

After moving all needed into the "in" folder back at the terminal which should be at the ~/nautilus_build/in$ prompt - 
```
sudo dpkg -i *.deb
```
Should complete without error, if there is it would be from adding to many or too little packages to the "in" folder. In that case adjust & rerun the above command **till it completes error free**. Then restart nautilus or log out/in & you should be good to go

---

### Post by Abandon on 2013-04-08
Wow! ;-) Its a bit too late for now but I will give this a try and learn something new, thats great. Thank you

---

### Post by Abandon on 2013-04-08
A big thank you! Thank you very much. It worked! I 'm happy and excited. :)  This is the perfect example why open source is the perfect . environment.

---

### Post by rrnbtter on 2013-04-08
Greetings,
I guess I don't know for sure what you are running. I had the same problem and had on vlc.desktop file. Fixing that solved the problem. I'm running 13.04 with the RC6 kernel. Have the 3.6 Nautilus and the open with option.

Glad you got it solved

---

### Post by mc4man on 2013-04-08
> **rrnbtter said:**
> Greetings,
I guess I don't know for sure what you are running. I had the same problem and had on vlc.desktop file. Fixing that solved the problem. I'm running 13.04 with the RC6 kernel. Have the 3.6 Nautilus and the open with option.

Glad you got it solved

Just to clear up for you - the issue isn't getting an open with on files, it's getting an open with thru nautilus on directories. That function was removed in nautilus-3.6 as being not needed
(or a convenience that isn't needed, sorta silly as it only occupies a few lines in one source file.

---

### Post by rrnbtter on 2013-04-08
Greetings,
I think I've got it! You want to play the contents of a media folder by clicking on the folder itself. The folder being mapped to VLC.  Thats a new one for me regarding Nautilus. I hope it comes back also. I can see where that would be useful. Sorry for the misunderstanding. I had to patch VLC just for it to show in the Open With right click menu and thought you had the same problem.

---

### Post by mc4man on 2013-04-08
> **jbicha said:**
>  If you just want to open videos with VLC, have you tried System Settings>Details>Default Applications ?

It's nice that at some point someone fixed that setting to actually be useful. (hadn't noticed till you mentioned.
 In the past it only set a default for one mimetype, in the case of video that would of been video/x-ogm+ogg. Now it sets chosen app as default for all 'known' video/* types. 
So in the case of files a useful settings option.

---

### Post by rrnbtter on 2013-04-08
Greetings,
Actually, I just duplicated the whole process in Krusader. I mapped a folder containing a set of vob files to VLC Media Player and when I right click on the folder I can choose VLC and it will then load and play the entire movie. This is a useful feature.

---

### Post by mc4man on 2013-04-11
nautilus updated to 15, it's a no nothing update that probably won't be any value to you, but is an update avail.
Still no time till weekend (tax stuff first) to explain how to patch directly, commit changes, ect. so you can take care of down the road yourself
(open with can also be re-enabled in nautilus-3.8

So if inclined, for simplicity's sake will attach a new debdiff. Just delete **all the files in nautilus_build **& do exactly as before except use this diff instead.
So only change would be patch command, use 
```
patch -Np1 -i ../nautilus_3.6.3-0ubuntu15.1.debdiff
```

(- would be nicer if Ubuntu just put this back, I guess only a few see the value, none that matter...
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254)

---

### Post by Abandon on 2013-04-11
You're the Hero! :popcorn:

---

### Post by teledyn on 2013-04-26
> **Abandon said:**
> A big thank you! Thank you very much. It worked! I 'm happy and excited. :)  This is the perfect example why open source is the perfect . environment.

Indeed it is, but it is also a perfect example of why open source is a hazardous environment as the cloistered developers can often make self-serving drastic work-flow disrupting changes that get propagated to everyone else.  I can't believe they'd do this, drop a major function without a deprecation period, it is wholly irresponsible.

but yes, we're not tied to them, are we. We could, we can and do, simply 'fix' their blunders back and trade that fix among those in the know, although that's too bad for the rest but here's hoping someone forks Nautilus and offers the Rest Of The World the same option ;)

Thanks for posting that fix, btw, much appreciated.  It isn't just VLC reading DVD images, but also Audacious, EasyTag and SoundConverter reading mp3 dirs, ImageMagick reading image dirs, Kino building a video clip collection, Emacs opening src dirs ... 

Really it is the whole paradigm of modern data-driven (not 80's era app driven) workflow, but I digress.

The other nice thing about an Open Source O/S is we can shop elsewhere with a mouse-click.  Anyone got any recommendations for alternative Unity file browsers? :D

---

### Post by mc4man on 2013-04-26
There are a whole host of good reasons to have open with in nautilus, but the Gnome devs & Ubuntu/Debian maintainers don't see it that way.
Attached is new debdiff for the .16, just use as before & adjust the patch command to reflect new  debdiff name 
```
 patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff
```

Never did get around to explaining how to manually patch, commit changes, ect. but for those that know, ect. will attach just the patch, line adjusted for the current .16 raring source (either use the debdiff or patch, not both...
nautilus 3.8 can also still be patched

---

### Post by Jean-Christophe Sekinger on 2013-04-30
1. I extracted the 2 files in folder nautilus_build
2. typed "patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff" in the terminal
3. but I have that error:
~/nautilus_build$ patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff
patch: **** Can't open patch file ../nautilus_3.6.3-0ubuntu16.1.debdiff : No such file or directory

what can I do?

---

### Post by dino99 on 2013-04-30
sudo apt-get install patch

---

### Post by Jean-Christophe Sekinger on 2013-04-30
Patch was already installed. The error message is the same :/

----
solved : [http://tinyurl.com/c7j89tb](http://tinyurl.com/c7j89tb)

---

### Post by mc4man on 2013-04-30
> **Jean-Christophe Sekinger said:**
> 1. I extracted the 2 files in folder nautilus_build
2. typed "patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff" in the terminal
3. but I have that error:<br>~/nautilus_build$ patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff<br>patch: **** Can't open patch file ../nautilus_3.6.3-0ubuntu16.1.debdiff : No such file or directory
what can I do?
This is basically the same mistake you were making on LP, that's why I suggested to come here & use the 2 posts I linked. You're  not at the proper terminal prompt when running the patch command

If you were to follow post 15 **exactly & completely **you'd be fine. So to repeat - start over, use all the commands in #15 except for the patch command, for that use what you were using 

patch -Np1 -i ../nautilus_3.6.3-0ubuntu16.1.debdiff

I also posted some screens in post 15 to help out & bolded some things,  look at them as you go, ect.

---

### Post by EgoGratis on 2013-04-30
I really don't like how i am not able to rearrange icons inside Nautilus from right click context menu anymore. Probably i was doing it wrong for decades?

Thank you GNOME you are the best!

---

### Post by EgoGratis on 2013-05-01
I think it's safe to say GNOME did wrong with:

-Removal of useful features from right click context menu and making it very basic and quite un-useful (i don't want to use the word useless).
-Removal of selecting drop-down options from connect to server dialogue and making it very basic and quite un-useful (i don't want to use the word useless).
-Removal of dual pane.
-Removal of...

It did OK with:

-Redesign of the GUI.
-Adding recursive search in.
-Adding...

It's safe to say in my opinion if GNOME would just do redesign and add some nice features it would do a lot of good but they decided they should remove a bunch of stuff and in my opinion they didn't have rationale to do it. It doesn't just affect small margin of users it affect probably the whole user base because a lot of small features where removed in small period of time.

What can we do about it? Not much i guess but that still doesn't mean they did the right thing.

---

### Post by Jean-Christophe Sekinger on 2013-05-01
Thank you but what means "You're  not at the proper terminal prompt"? Excuse-me I'm a newbie and my english is very poor :]
--- well I undestood :|

---

### Post by monkeybrain2012 on 2013-05-01
> **Jean-Christophe Sekinger said:**
> Thank you but what means "You're  not at the proper terminal prompt"? Excuse-me I'm a newbie and my english is very poor :]

The prompt should be "~/nautilus_build/nautilus-3.6.3$" It means you should first change your directory into this directory before you execute the patch command. Before you run the patch you are one level up in the directory ~/nautilus_build (see your prompt)

so  to change directory to the subdirectory ~/nautilus_build/nautilus-3.6.3  you first type

```
cd nautilus-3.6.3
```

And then run the patch command.


EDITED: by default when you start the terminal you are always in /Home/yourusername ( which is the same as ~/) and you move to a subdirectory using the cd command followed by the path after yourusename. So to change directory into some folder on the  desktop (~/Desktop/foldername) you do "cd Desktop/foldername" etc. (you can omit the ~/ if you start out in your home directory)
"cd .. " means going one level up from your current directory. so if you see the prompt  "~/nautilus_build/nautilus-3.6.3$", running "cd .." (without quote) would bring you to ~/nautilus_build and the prompt would become just  "~/nautilus_build$"

---

### Post by Jean-Christophe Sekinger on 2013-05-01
@mc4man: Every thing was right! Many many thanks!

---

### Post by kevpan815 on 2013-05-01
> **Jean-Christophe Sekinger said:**
> @mc4man: Every thing was right! Many many thanks!

Please stop all disscusions of 13.04 in this Ubuntu + 1 Sub-Forums. Now that the 13.10 Nightly Builds are up on the CDImage.Ubuntu.Com Download Server, you should only be Discussing 13.10 in this Ubuntu + 1 Sub-Forum. Otherwise I will have to start Reporting Posts that continue to Discuss 13.04 in this Ubuntu + 1 Sub-Forum! This is your Final Warning!

---

### Post by cariboo on 2013-05-01
> **kevpan815 said:**
> Please stop all disscusions of 13.04 in this Ubuntu + 1 Sub-Forums. Now that the 13.10 Nightly Builds are up on the CDImage.Ubuntu.Com Download Server, you should only be Discussing 13.10 in this Ubuntu + 1 Sub-Forum. Otherwise I will have to start Reporting Posts that continue to Discuss 13.04 in this Ubuntu + 1 Sub-Forum! This is your Final Warning!


Officially Saucy development doesn't start until Thursday May 2, see the release schedule [here]("https://wiki.ubuntu.com/SaucySalamander/ReleaseSchedule"), and even then there are many issues that are being brought forward from the current release, so I feel these conversations are still relevant.

---

