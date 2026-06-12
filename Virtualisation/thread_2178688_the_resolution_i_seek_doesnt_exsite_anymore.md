---
title: "the resolution i seek doesnt exsite anymore"
date: 2013-10-04
forum: Virtualisation
---

### Post by kingston_middleton on 2013-10-04
```
kingston@Hal-II:~$ xrandrScreen 0: minimum 320 x 200, current 848 x 480, maximum 8192 x 8192LVDS connected 848x480+0+0 (normal left inverted right x axis y axis) 344mm x 194mm   848x480        59.7*    720x480        59.7     640x480        59.4  VGA-0 disconnected (normal left inverted right x axis y axis)kingston@Hal-II:~$ xrandr screen 0:1280x768usage: xrandr [options]  where options are:  -display <display> or -d <display>  -help  -o <normal,inverted,left,right,0,1,2,3>            or --orientation <normal,inverted,left,right,0,1,2,3>  -q        or --query  -s <size>/<width>x<height> or --size <size>/<width>x<height>  -r <rate> or --rate <rate> or --refresh <rate>  -v        or --version  -x        (reflect in x)  -y        (reflect in y)  --screen <screen>  --verbose  --current  --dryrun  --nograb  --prop or --properties  --fb <width>x<height>  --fbmm <width>x<height>  --dpi <dpi>/<output>  --output <output>      --auto      --mode <mode>      --preferred      --pos <x>x<y>      --rate <rate> or --refresh <rate>      --reflect normal,x,y,xy      --rotate normal,inverted,left,right      --left-of <output>      --right-of <output>      --above <output>      --below <output>      --same-as <output>      --set <property> <value>      --scale <x>x<y>      --scale-from <w>x<h>      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>      --off      --crtc <crtc>      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]      --gamma <r>:<g>:<b>      --primary  --noprimary  --newmode <name> <clock MHz>            <hdisp> <hsync-start> <hsync-end> <htotal>            <vdisp> <vsync-start> <vsync-end> <vtotal>            [flags...]            Valid flags: +HSync -HSync +VSync -VSync                         +CSync -CSync CSync Interlace DoubleScan  --rmmode <name>  --addmode <output> <name>  --delmode <output> <name>  --listproviders  --setprovideroutputsource <prov-xid> <source-xid>  --setprovideroffloadsink <prov-xid> <sink-xid>

```

ok so thats alot of code but here my problem this thing is hurting my eyes with this bad resolution.
i need a 1366x800 or somthing bigger and i cant find any code that will fix this, if somone has a code that i can use to make a new resolution in the setting i would like to have it.

i downloaded avogadro and it killed my old nivida card and put a new differnt nivida card in killing my old resolution settings and setting new smaller ones. and i cant get it to be bigger anymore.

thanks for any help.
Kingston

---

### Post by Habitual on 2013-10-04
re-run ```
nvidia-settings 
``` ?

---

