---
title: "Bootfighter Windom XP Graphics issue"
date: 2009-07-25
forum: Wine
---

### Post by Aud1o Blood on 2009-07-25
Okay, semi-new guy here.

I installed wine, ran the installer for Bootfighter.
After it failed to work, I used winetricks to add the .dll-s on this list:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13387](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13387)

I got the program to open, but when I go to play, it displays the status bars--but no surrounding scenery (or the mech).
I think this is the shadow issue, but I don't know how to fix it.


He said go into config.ini--and mess with that, but I don't know what to change.

Here are the contents of config.ini
```
[Window]

FullScreen=0

w=1024

h=768



[D3DSetting]

TextureLevel=0



[GameSetting]

MaxFrameSkip=5

Far=5

DisableShader=0

Shadow=2

HDR=1

DefaultIP=127.0.0.1

DefaultName=



KEY_¶=37

KEY_ã=38

KEY_&#137;E=39

KEY_&#137;º=40

KEY_&#131;W&#131;&#131;&#131;&#147;&#131;v=90

KEY_&#131;V&#131;&#135;&#131;b&#131;g=88

KEY_&#131;T[&#131;x&#131;&#139;=67

KEY_&#131;^&#131;Q&#149;ÏX=83

KEY_&#131;K[&#131;h=86

KEY_&#131;T&#131;u&#130;P=65

KEY_&#131;T&#131;u&#130;Q=68

KEY_&#131;T&#131;u&#130;R=70



JOY_&#131;W&#131;&#131;&#131;&#147;&#131;v=3

JOY_&#131;V&#131;&#135;&#131;b&#131;g=1

JOY_&#131;T[&#131;x&#131;&#139;=2

JOY_&#131;^&#131;Q&#149;ÏX=4

JOY_&#131;K[&#131;h=6

JOY_&#131;T&#131;u&#130;P=5

JOY_&#131;T&#131;u&#130;Q=7

JOY_&#131;T&#131;u&#130;R=8

JOY_START=10

JOY_CANCEL=9

PMQuality=0

VolumeBGM=100

VolumeSE=100

VolumeVOICE=100

```

Please help if you can.

Also, if you stumble while trying to install the dll files, go to the wiki page for winetricks:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

