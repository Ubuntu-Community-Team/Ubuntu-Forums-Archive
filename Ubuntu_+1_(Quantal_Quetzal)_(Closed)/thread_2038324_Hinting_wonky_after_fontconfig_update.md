---
title: "Hinting wonky after fontconfig update?"
date: 2012-08-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by outZider on 2012-08-06
fontconfig went to 2.10.1-0ubuntu2, and it looks like my hinting is all off now. I have (or had) autohint, medium hinting, and rgb subpixel on, but it looks like all of my custom stuff is shut off. Anyone else run into this?

---

### Post by outZider on 2012-08-06
OK, to revise. It does keep settings, but medium and full hinting seems different, and in my view, broken, after that update.

---

### Post by outZider on 2012-08-06
Also confirming that a downgrade to 2.8.0-3ubuntu9 made things work normally again. :)

---

### Post by VinDSL on 2012-08-06
Can't say that I've experienced any display problems, but...

I'm getting errors up the ying-yang now, in CLI.

Example:  Just installed "lightread" (Ubu app-review-board PPA)...


```
<snip>

Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
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
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-unfonts-core.conf", line 11: Having multiple values in <test> isn't supported and may not works as expected
Selecting previously unselected package libjs-underscore.
(Reading database ... 438736 files and directories currently installed.)
Unpacking libjs-underscore (from .../libjs-underscore_1.3.3-1ubuntu1_all.deb) ...
Selecting previously unselected package lightread.
Unpacking lightread (from .../lightread_1.0.14-0extras12.04.1_all.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Setting up libjs-underscore (1.3.3-1ubuntu1) ...
Setting up lightread (1.0.14-0extras12.04.1) ...


```

Guess it doesn't "works as expected" for us.  :)

---

### Post by VinDSL on 2012-08-06
Heh!  That Google Reader is pretty sharp!

Anyway, here's how my fonts look...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-6-aug-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-aug-2012-2.png")[/INDENT]

---

### Post by flipper T on 2012-08-06
vindsl, i have been getting same error messages since upgrade & when opening chrome or rhythmbox.

moved offending fonts to rubbish bin. no obvious side effects.

ps do you actually have your active window that small to show your conky ? :)

perhaps an additional monitor screen is required for that beast :)

---

### Post by VinDSL on 2012-08-06
> **flipper T said:**
> ps do you actually have your active window that small to show your conky ? :)

perhaps an additional monitor screen is required for that beast :)
Heh!  Yeah, I need a bigger monitor...  :)

---

### Post by flipper T on 2012-08-06
or a smaller conky ?

ignore me, i have conky-envy. probably mid-life crisis :)

---

### Post by cecilpierce on 2012-08-07
I get a lot of these in a terminal window at first boot, is it a bug ? 
> Fontconfig warning: "/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf", line 9: H
aving multiple values in <test> isn't supported and may not works as expected


---

### Post by stinkeye on 2012-08-07
Getting same errors when running conky with some downloaded fonts.
The font just appears as a box in conky.

When I open the fonts they don't show the same as in precise.

In precise...
[ATTACH]222375[/ATTACH]


In Quantal...
[ATTACH]222376[/ATTACH]

---

### Post by 3vi1 on 2012-08-07
Same issue here...  Conky looks fine, but I see that error many times when starting it.

---

### Post by stinkeye on 2012-08-07
This shows a conky using the ConkySymbols font (coloured blue) 
and the CD Numbers font(coloured pink) on both 11.10 and 12.04.

---

### Post by VinDSL on 2012-08-09
**_UPDATE_**

I fixed the fontconfig *warnings* by manually editing the errant .conf files.

The "trick" was to do away with nesting in various sections of the new fontconfig .conf files in /etc/fonts/conf.d

For instance, in /etc/fonts/conf.d/65-droid-sans-fonts.conf:

I converted this...

```
  <match target="scan">
[B][COLOR="DarkRed"]    <test name="lang">
      <string>zh-cn</string>
      <string>zh-sg</string>
      <string>zh-hk</string>
      <string>zh-tw</string>
      <string>zh</string>
    </test>[/COLOR][/B]
    <test name="family">
      <string>Droid Sans Japanese</string>
    </test>
    <edit name="family">
      <string>Droid Sans</string>
    </edit>
    <edit name="fullname">
      <string>Droid Sans</string>
    </edit>
    <edit name="fontversion">
      <int>1</int>
    </edit>
  </match>
```

...into this.

```
  <match target="scan">
[B][COLOR="DarkRed"]    <test name="lang">
      <string>zh-cn</string>
    </test>
    <test name="lang">
      <string>zh-sg</string>
    </test>
    <test name="lang">
      <string>zh-hk</string>
    </test>
    <test name="lang">
      <string>zh-tw</string>
    </test>
    <test name="lang">
      <string>zh</string>
    </test>[/COLOR][/B]
    <test name="family">
      <string>Droid Sans Japanese</string>
    </test>
    <edit name="family">
      <string>Droid Sans</string>
    </edit>
    <edit name="fullname">
      <string>Droid Sans</string>
    </edit>
    <edit name="fontversion">
      <int>1</int>
    </edit>
  </match>
```

I also did away with the .fonts.conf file & ~/.fontconfig folder (special thanks to dino99).

I haven't been having any font rendering problems, but the above method took care of all the errors in CLI.

Soooo, all is good again!  :)


```
vindsl@Zuul:~$ apt-cache policy fontconfig
fontconfig:
  Installed: 2.10.1-0ubuntu2
  Candidate: 2.10.1-0ubuntu2
  Version table:
 *** 2.10.1-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ xdpyinfo | grep -E '(resolution|dimensions)'
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ fc-match --all
DejaVuSans.ttf: "DejaVu Sans" "Book"
DejaVuSansCondensed.ttf: "DejaVu Sans" "Condensed"
DejaVuSans-ExtraLight.ttf: "DejaVu Sans" "ExtraLight"
DejaVuSans-Bold.ttf: "DejaVu Sans" "Bold"
DejaVuSansCondensed-Bold.ttf: "DejaVu Sans" "Condensed Bold"
DejaVuSans-Oblique.ttf: "DejaVu Sans" "Oblique"
DejaVuSansCondensed-Oblique.ttf: "DejaVu Sans" "Condensed Oblique"
DejaVuSans-BoldOblique.ttf: "DejaVu Sans" "Bold Oblique"
DejaVuSansCondensed-BoldOblique.ttf: "DejaVu Sans" "Condensed Bold Oblique"
n019003l.pfb: "Nimbus Sans L" "Regular"
n019043l.pfb: "Nimbus Sans L" "Regular Condensed"
n019004l.pfb: "Nimbus Sans L" "Bold"
n019044l.pfb: "Nimbus Sans L" "Bold Condensed"
n019023l.pfb: "Nimbus Sans L" "Regular Italic"
n019063l.pfb: "Nimbus Sans L" "Regular Condensed Italic"
n019024l.pfb: "Nimbus Sans L" "Bold Italic"
n019064l.pfb: "Nimbus Sans L" "Bold Condensed Italic"
Waree.ttf: "Waree" "Book"
Waree-Bold.ttf: "Waree" "Bold"
Waree-Oblique.ttf: "Waree" "Oblique"
Waree-BoldOblique.ttf: "Waree" "BoldOblique"
Loma.ttf: "Loma" "Book"
Loma-Bold.ttf: "Loma" "Bold"
Loma-Oblique.ttf: "Loma" "Oblique"
Loma-BoldOblique.ttf: "Loma" "BoldOblique"
Garuda.ttf: "Garuda" "Book"
Garuda-Bold.ttf: "Garuda" "Bold"
Garuda-Oblique.ttf: "Garuda" "Oblique"
Garuda-BoldOblique.ttf: "Garuda" "BoldOblique"
Umpush.ttf: "Umpush" "Book"
Umpush-Light.ttf: "Umpush" "Light"
Umpush-Bold.ttf: "Umpush" "Bold"
Umpush-Oblique.ttf: "Umpush" "Oblique"
Umpush-LightOblique.ttf: "Umpush" "LightOblique"
Umpush-BoldOblique.ttf: "Umpush" "BoldOblique"
KhmerOS.ttf: "Khmer OS" "Regular"
MuktiNarrow.ttf: "Mukti Narrow" "Regular"
MuktiNarrowBold.ttf: "Mukti Narrow" "Regular"
NanumGothic.ttf: "NanumGothic" "Regular"
NanumGothicBold.ttf: "NanumGothic" "Bold"
UnDotum.ttf: "UnDotum" "Regular"
UnDotumBold.ttf: "UnDotum" "Bold"
lohit_bn.ttf: "Lohit Bengali" "Regular"
lohit_gu.ttf: "Lohit Gujarati" "Regular"
lohit_hi.ttf: "Lohit Hindi" "Regular"
lohit_pa.ttf: "Lohit Punjabi" "Regular"
lohit_ta.ttf: "Lohit Tamil" "Regular"
Meera_04.ttf: "Meera" "Regular"
FreeSans.ttf: "FreeSans" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
FreeSansBold.ttf: "FreeSans" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
FreeSansOblique.ttf: "FreeSans" "&#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
FreeSansBoldOblique.ttf: "FreeSans" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
TlwgTypo.ttf: "Tlwg Typo" "Medium"
KacstArt.ttf: "KacstArt" "Medium"
KacstBook.ttf: "KacstBook" "Medium"
KacstDecorative.ttf: "KacstDecorative" "Medium"
KacstDigital.ttf: "KacstDigital" "Medium"
KacstFarsi.ttf: "KacstFarsi" "Medium"
KacstLetter.ttf: "KacstLetter" "Medium"
KacstNaskh.ttf: "KacstNaskh" "Medium"
KacstOffice.ttf: "KacstOffice" "Medium"
KacstPen.ttf: "KacstPen" "Medium"
KacstPoster.ttf: "KacstPoster" "Medium"
KacstScreen.ttf: "KacstScreen" "Medium"
KacstTitle.ttf: "KacstTitle" "Medium"
gargi.ttf: "gargi" "Medium"
TlwgTypist.ttf: "Tlwg Typist" "Medium"
TlwgMono.ttf: "TlwgMono" "Medium"
TlwgTypewriter.ttf: "TlwgTypewriter" "Medium"
Kinnari.ttf: "Kinnari" "Medium"
ConkyWeather.otf: "ConkyWeather" "Medium"
ConkyWind.otf: "ConkyWind" "Medium"
ConkyWindN.otf: "ConkyWindN" "Medium"
ConkyWindNESW.otf: "ConkyWindNESW" "Medium"
Rekha.ttf: "Rekha" "Medium"
utkal.ttf: "ori1Uni" "Medium"
Ubuntu-M.ttf: "Ubuntu" "Medium"
c059013l.pfb: "Century Schoolbook L" "Roman"
p052003l.pfb: "URW Palladio L" "Roman"
FreeMono.ttf: "FreeMono" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
FreeSerif.ttf: "FreeSerif" "&#1085;&#1086;&#1088;&#1084;&#1072;&#1083;&#1077;&#1085;"
opens___.ttf: "OpenSymbol" "Regular"
KacstOne.ttf: "KacstOne" "Regular"
Norasi.ttf: "Norasi" "Regular"
Rachana_04.ttf: "Rachana" "Regular"
fonts-japanese-gothic.ttf: "TakaoPGothic" "Regular"
TakaoPGothic.ttf: "TakaoPGothic" "Regular"
KhmerOSsys.ttf: "Khmer OS System" "Regular"
DejaVuSansMono.ttf: "DejaVu Sans Mono" "Book"
DejaVuSerif.ttf: "DejaVu Serif" "Book"
NanumMyeongjo.ttf: "NanumMyeongjo" "Regular"
Purisa.ttf: "Purisa" "Medium"
KacstQurn.ttf: "KacstQurn" "Medium"
KacstTitleL.ttf: "KacstTitleL" "Medium"
Radiof.ttf: "Radio Space" "Regular"
UbuntuTitleBold.ttf: "UbuntuTitleBold" "Bold"
UbuntuTitleRegular.ttf: "UbuntuTitleRegular" "Regular"
Ubuntu-Title.ttf: "Ubuntu-Title" "Title"
Pothana2000.ttf: "Pothana2000" "Pothana2000"
Vemana.ttf: "Vemana2000" "Pothana2000"
LiberationMono-Regular.ttf: "Liberation Mono" "Regular"
LiberationSans-Regular.ttf: "Liberation Sans" "Regular"
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"
LiberationMono-Regular.ttf: "Liberation Mono" "Regular"
LiberationSans-Regular.ttf: "Liberation Sans" "Regular"
LiberationSerif-Regular.ttf: "Liberation Serif" "Regular"
Sawasdee.ttf: "Sawasdee" "Regular"
mry_KacstQurn.ttf: "mry_KacstQurn" "Regular"
Overlock-Regular-OTF.otf: "Overlock" "Regular"
Ahem.ttf: "Ahem" "Regular"
DroidSansMono.ttf: "Droid Sans Mono" "Regular"
DroidSerif-Regular.ttf: "Droid Serif" "Regular"
DroidSansMono.ttf: "Droid Sans Mono" "Regular"
DroidSerif-Regular.ttf: "Droid Serif" "Regular"
Phetsarath_OT.ttf: "Phetsarath OT" "Regular"
UnDinaru.ttf: "UnDinaru" "Regular"
BOXES.TTF: "Some Boxes" "Regular"
BOXES.TTF: "Some Boxes" "Regular"
KR A Round.ttf: "KR A Round" "Regular"
PIZZADUDEBULLETS.ttf: "PizzaDude Bullets" "Regular"
STYLBCC_.TTF: "StyleBats" "CleanCut"
cutouts.ttf: "Cut Outs for 3D FX" "Normal"
openlogos.ttf: "OpenLogos" "Regular"
Arrows.ttf: "Arrows" "Regular"
StyleBats.ttf: "StyleBats" "CleanCut"
Kedage-n.ttf: "Kedage" "Normal"
Malige-n.ttf: "Mallige" "Normal"
cutouts.ttf: "Cut Outs for 3D FX" "Normal"
Ubuntu-C.ttf: "Ubuntu Condensed" "Regular"
Ubuntu-R.ttf: "Ubuntu" "Regular"
UbuntuMono-R.ttf: "Ubuntu Mono" "Regular"
wqy-microhei.ttc: "WenQuanYi Micro Hei" "Regular"
wqy-microhei.ttc: "WenQuanYi Micro Hei Mono" "Regular"
Saab.ttf: "Saab" "Regular"
Ubuntu-R.ttf: "Ubuntu" "Regular"
DroidSans.ttf: "Droid Sans" "Regular"
DroidSans.ttf: "Droid Sans" "Regular"
DroidNaskh-Regular.ttf: "Droid Sans" "Regular"
DroidSansEthiopic-Regular.ttf: "Droid Sans" "Regular"
DroidSansHebrew-Regular.ttf: "Droid Sans" "Regular"
DroidSansThai.ttf: "Droid Sans" "Regular"
DroidSansArmenian.ttf: "Droid Sans" "Regular"
DroidSansGeorgian.ttf: "Droid Sans" "Regular"
DroidSansJapanese.ttf: "Droid Sans" "Regular"
DroidSansJapanese.ttf: "Droid Sans" "Regular"
DroidSansFallback.ttf: "Droid Sans" "Regular"
DroidSansFallbackFull.ttf: "Droid Sans" "Regular"
c0419bt_.pfb: "Courier 10 Pitch" "Regular"
c0648bt_.pfb: "Bitstream Charter" "Regular"
UnBatang.ttf: "UnBatang" "Regular"
UnGraphic.ttf: "UnGraphic" "Regular"
UnGungseo.ttf: "UnGungseo" "Regular"
UnPilgi.ttf: "UnPilgi" "Regular"
b018012l.pfb: "URW Bookman L" "Light"
n021003l.pfb: "Nimbus Roman No9 L" "Regular"
n022003l.pfb: "Nimbus Mono L" "Regular"
MOON.TTF: "Moon Phases" "Regular"
Symbol.pfb: "Symbol" "Regular"
Moon Phases.ttf: "Moon Phases" "Regular"
d050000l.pfb: "Dingbats" "Regular"
s050000l.pfb: "Standard Symbols L" "Regular"
Symbol.pfb: "Symbol" "Regular"
DejaVuSerifCondensed.ttf: "DejaVu Serif" "Condensed"
Radiofc.ttf: "Radio Space Condensed" "Condensed"
LiberationSansNarrow-Regular.ttf: "Liberation Sans Narrow" "Regular"
LiberationSansNarrow-Regular.ttf: "Liberation Sans Narrow" "Regular"
a010013l.pfb: "URW Gothic L" "Book"
UnDinaruLight.ttf: "UnDinaru" "Light"
Ubuntu-L.ttf: "Ubuntu" "Light"
Ubuntu-L.ttf: "Ubuntu" "Light"
DroidSansHebrew-Bold.ttf: "Droid Sans" "Bold"
a010015l.pfb: "URW Gothic L" "Demi"
FreeSerifBold.ttf: "FreeSerif" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
FreeMonoBold.ttf: "FreeMono" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085;"
KacstOne-Bold.ttf: "KacstOne" "Bold"
Norasi-Bold.ttf: "Norasi" "Bold"
DejaVuSansMono-Bold.ttf: "DejaVu Sans Mono" "Bold"
DejaVuSerif-Bold.ttf: "DejaVu Serif" "Bold"
Purisa-Bold.ttf: "Purisa" "Bold"
TlwgTypo-Bold.ttf: "Tlwg Typo" "Bold"
Radiofb.ttf: "Radio Space Bold" "Bold"
LiberationMono-Bold.ttf: "Liberation Mono" "Bold"
LiberationSans-Bold.ttf: "Liberation Sans" "Bold"
LiberationSerif-Bold.ttf: "Liberation Serif" "Bold"
LiberationMono-Bold.ttf: "Liberation Mono" "Bold"
LiberationSans-Bold.ttf: "Liberation Sans" "Bold"
LiberationSerif-Bold.ttf: "Liberation Serif" "Bold"
TlwgTypist-Bold.ttf: "Tlwg Typist" "Bold"
TlwgMono-Bold.ttf: "TlwgMono" "Bold"
TlwgTypewriter-Bold.ttf: "TlwgTypewriter" "Bold"
Kinnari-Bold.ttf: "Kinnari" "Bold"
Sawasdee-Bold.ttf: "Sawasdee" "Bold"
DroidSerif-Bold.ttf: "Droid Serif" "Bold"
DroidSerif-Bold.ttf: "Droid Serif" "Bold"
UnDinaruBold.ttf: "UnDinaru" "Bold"
weather.ttf: "Weather" "Regular"
weather.ttf: "Weather" "Regular"
wef_____.ttf: "Weather" "Regular"
NanumMyeongjoBold.ttf: "NanumMyeongjo" "Bold"
Kedage-b.ttf: "Kedage" "Bold"
Malige-b.ttf: "Mallige" "Bold"
Ubuntu-B.ttf: "Ubuntu" "Bold"
UbuntuMono-B.ttf: "Ubuntu Mono" "Bold"
Ubuntu-B.ttf: "Ubuntu" "Bold"
DroidSans-Bold.ttf: "Droid Sans" "Bold"
DroidSans-Bold.ttf: "Droid Sans" "Bold"
DroidNaskh-Bold.ttf: "Droid Sans" "Bold"
DroidSansEthiopic-Bold.ttf: "Droid Sans" "Bold"
c0583bt_.pfb: "Courier 10 Pitch" "Bold"
c0632bt_.pfb: "Bitstream Charter" "Bold"
UnBatangBold.ttf: "UnBatang" "Bold"
UnGraphicBold.ttf: "UnGraphic" "Bold"
UnPilgiBold.ttf: "UnPilgi" "Bold"
b018015l.pfb: "URW Bookman L" "Demi Bold"
c059016l.pfb: "Century Schoolbook L" "Bold"
n021004l.pfb: "Nimbus Roman No9 L" "Medium"
n022004l.pfb: "Nimbus Mono L" "Bold"
p052004l.pfb: "URW Palladio L" "Bold"
DejaVuSerifCondensed-Bold.ttf: "DejaVu Serif" "Condensed Bold"
LiberationSansNarrow-Bold.ttf: "Liberation Sans Narrow" "Bold"
LiberationSansNarrow-Bold.ttf: "Liberation Sans Narrow" "Bold"
Kinnari-Italic.ttf: "Kinnari" "Italic"
Ubuntu-MI.ttf: "Ubuntu" "Medium Italic"
z003034l.pfb: "URW Chancery L" "Medium Italic"
FreeSerifItalic.ttf: "FreeSerif" "&#1082;&#1091;&#1088;&#1089;&#1080;&#1074;&#1077;&#1085;"
FreeMonoOblique.ttf: "FreeMono" "&#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
Norasi-Italic.ttf: "Norasi" "Italic"
DejaVuSerif-Italic.ttf: "DejaVu Serif" "Italic"
Radiofi.ttf: "Radio Space Italic" "Italic"
LiberationMono-Italic.ttf: "Liberation Mono" "Italic"
LiberationSans-Italic.ttf: "Liberation Sans" "Italic"
LiberationSerif-Italic.ttf: "Liberation Serif" "Italic"
LiberationMono-Italic.ttf: "Liberation Mono" "Italic"
LiberationSans-Italic.ttf: "Liberation Sans" "Italic"
LiberationSerif-Italic.ttf: "Liberation Serif" "Italic"
DroidSerif-Italic.ttf: "Droid Serif" "Italic"
DroidSerif-Italic.ttf: "Droid Serif" "Italic"
Ubuntu-RI.ttf: "Ubuntu" "Italic"
UbuntuMono-RI.ttf: "Ubuntu Mono" "Italic"
Ubuntu-RI.ttf: "Ubuntu" "Italic"
c0582bt_.pfb: "Courier 10 Pitch" "Italic"
c0649bt_.pfb: "Bitstream Charter" "Italic"
b018032l.pfb: "URW Bookman L" "Light Italic"
c059033l.pfb: "Century Schoolbook L" "Italic"
n021023l.pfb: "Nimbus Roman No9 L" "Regular Italic"
p052023l.pfb: "URW Palladio L" "Italic"
DejaVuSerifCondensed-Italic.ttf: "DejaVu Serif" "Condensed Italic"
LiberationSansNarrow-Italic.ttf: "Liberation Sans Narrow" "Italic"
LiberationSansNarrow-Italic.ttf: "Liberation Sans Narrow" "Italic"
Ubuntu-LI.ttf: "Ubuntu" "Light Italic"
Ubuntu-LI.ttf: "Ubuntu" "Light Italic"
FreeSerifBoldItalic.ttf: "FreeSerif" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1082;&#1091;&#1088;&#1089;&#1080;&#1074;&#1077;&#1085;"
FreeMonoBoldOblique.ttf: "FreeMono" "&#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1088;&#1077;&#1085; &#1085;&#1072;&#1082;&#1083;&#1086;&#1085;&#1077;&#1085;"
Norasi-BoldItalic.ttf: "Norasi" "BoldItalic"
DejaVuSerif-BoldItalic.ttf: "DejaVu Serif" "Bold Italic"
Radiofbi.ttf: "Radio Space Bold Italic" "Bold Italic"
LiberationMono-BoldItalic.ttf: "Liberation Mono" "Bold Italic"
LiberationSans-BoldItalic.ttf: "Liberation Sans" "Bold Italic"
LiberationSerif-BoldItalic.ttf: "Liberation Serif" "Bold Italic"
LiberationMono-BoldItalic.ttf: "Liberation Mono" "Bold Italic"
LiberationSans-BoldItalic.ttf: "Liberation Sans" "Bold Italic"
LiberationSerif-BoldItalic.ttf: "Liberation Serif" "Bold Italic"
Kinnari-BoldItalic.ttf: "Kinnari" "BoldItalic"
DroidSerif-BoldItalic.ttf: "Droid Serif" "Bold Italic"
DroidSerif-BoldItalic.ttf: "Droid Serif" "Bold Italic"
Ubuntu-BI.ttf: "Ubuntu" "Bold Italic"
UbuntuMono-BI.ttf: "Ubuntu Mono" "Bold Italic"
Ubuntu-BI.ttf: "Ubuntu" "Bold Italic"
c0611bt_.pfb: "Courier 10 Pitch" "Bold Italic"
c0633bt_.pfb: "Bitstream Charter" "Bold Italic"
b018035l.pfb: "URW Bookman L" "Demi Bold Italic"
c059036l.pfb: "Century Schoolbook L" "Bold Italic"
n021024l.pfb: "Nimbus Roman No9 L" "Medium Italic"
p052024l.pfb: "URW Palladio L" "Bold Italic"
DejaVuSerifCondensed-BoldItalic.ttf: "DejaVu Serif" "Condensed Bold Italic"
LiberationSansNarrow-BoldItalic.ttf: "Liberation Sans Narrow" "Bold Italic"
LiberationSansNarrow-BoldItalic.ttf: "Liberation Sans Narrow" "Bold Italic"
TlwgTypo-Oblique.ttf: "Tlwg Typo" "Oblique"
TlwgTypist-Oblique.ttf: "Tlwg Typist" "Oblique"
Kinnari-Oblique.ttf: "Kinnari" "Oblique"
Norasi-Oblique.ttf: "Norasi" "Oblique"
DejaVuSansMono-Oblique.ttf: "DejaVu Sans Mono" "Oblique"
Purisa-Oblique.ttf: "Purisa" "Oblique"
TlwgMono-Oblique.ttf: "TlwgMono" "Oblique"
TlwgTypewriter-Oblique.ttf: "TlwgTypewriter" "Oblique"
Sawasdee-Oblique.ttf: "Sawasdee" "Oblique"
n022023l.pfb: "Nimbus Mono L" "Regular Oblique"
a010033l.pfb: "URW Gothic L" "Book Oblique"
a010035l.pfb: "URW Gothic L" "Demi Oblique"
Norasi-BoldOblique.ttf: "Norasi" "BoldOblique"
DejaVuSansMono-BoldOblique.ttf: "DejaVu Sans Mono" "Bold Oblique"
Purisa-BoldOblique.ttf: "Purisa" "BoldOblique"
TlwgTypo-BoldOblique.ttf: "Tlwg Typo" "BoldOblique"
TlwgTypist-BoldOblique.ttf: "Tlwg Typist" "BoldOblique"
TlwgMono-BoldOblique.ttf: "TlwgMono" "BoldOblique"
TlwgTypewriter-BoldOblique.ttf: "TlwgTypewriter" "BoldOblique"
Kinnari-BoldOblique.ttf: "Kinnari" "BoldOblique"
Sawasdee-BoldOblique.ttf: "Sawasdee" "BoldOblique"
n022024l.pfb: "Nimbus Mono L" "Bold Oblique"
vindsl@Zuul:~$ 

```

---

### Post by VinDSL on 2012-08-09
> **cecilpierce said:**
> I get a lot of these in a terminal window at first boot, is it a bug ?IMO, it's not necessarily a bug.

I *think* it has more to do with way the logical functions (AND, and/or, OR) in various programs are handling the nested sections.

The "quick fix" is to do away with the nesting. ;)

---

### Post by outZider on 2012-08-09
So, still having the same thing. Slight/No hinting seem to show up mostly okay, but Medium and Full go full-butt. I'm set to Medium hinting, rgba lcd rendering. Enclosed is a before shot, from 2.8.0-3ubuntu9, and after, from 2.10.1-0ubuntu2.

---

### Post by Sworddragon on 2012-08-23
> **VinDSL said:**
> I haven't been having any font rendering problems, but the above method took care of all the errors in CLI.

I have made a few tests some days ago and looked for information how the font files are working. As I know all entries in <match> must be true. Theoretically this can never happen if it contains 2 or more font names. The correct solution should be to use for every font name an own <match>.

There is no warranty of this post. Maybe somebody else knows more about this and has a better solution. At least using just a <test> for every font hasn't worked for me.

---

