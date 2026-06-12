---
title: "Hinting / Antialiasing / fonts broken?"
date: 2012-09-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-01
I'm using professional IPS monitors properly adjusted to reduce eye strain. It's not a problem with the monitors (unless it affected two monitors simultaneously). Something seems to have happened to hinting / antialiasing / fonts / something with latest updates. Text is now grainier than my Kindle DX. 

This is particularly noticeable in PDFs using Adobe Reader or Document Viewer. Google Chrome and Chromium seem to render fonts a little better but still not normally. Firefox / Thunderbird fonts look just awful. Dash text is also looking not properly rendered.

Hinting is set to "Slight" and "Antialiasing" is set to "rgba". I have tried Hinting = None/Slight/Medium/Full vs AA = None / rgba / Grayscale 12 combinations and all are worse than Slight+rgba anyway.

Considering we had some font problems recently, I was wondering if anyone knew of a workaround. I already have enough daily headaches with normal fonts. 

Regards,
Effenberg

---

### Post by coffeecat on 2012-09-01
I don't have the classy monitors you have :) - just two different Sony Vaio laptops running Quantal, with whatever LCD panels Sony uses. One has Intel graphics, the other nvidia with the ppa 304.43 proprietary driver, both fully updated this morning. I've only checked firefox and the dash so far, but font rendering seems to be as good as it has been.

I'll keep a watch out in case it was an update that has caused your issue, and in case the update hasn't got to the update server I use.

---

### Post by VinDSL on 2012-09-01
> **effenberg0x0 said:**
> Considering we had some font problems recently, I was wondering if anyone knew of a workaround.[...]
I had this problem, a week or two ago.  Matter of fact, a lot of ppl were complaining about it, during the nVidia escapades.

At that time, I couldn't even log into Unity/GS, but the poor rendering quality was driving my eyes buggy in LXDE/Openbox.

The "cure" in LXDE was to install a compositor. I chose XCompMgr, and the difference was jaw-dropping.

Haven't had a prob in Unity, so fiddling around with the compositing/compositor effects hasn't been required.


Just saying...

---

### Post by effenberg0x0 on 2012-09-01
> **coffeecat said:**
> I don't have the classy monitors you have :) - just two different Sony Vaio laptops running Quantal, with whatever LCD panels Sony uses. 

There are 4 panel manufacturers (3 groups, actually) that manufacture 90% of the world's panels. Each has 2 to 4 tiers of panels (for low-end, standard, high-end monitors/laptops). Sony gets first tier high quality TN panels. I got this two Dell U2412M from a client as part of a payment for small IT services. Actually, I get a large part of my hardware that way :) Anyway, I recently invested in getting this professional monitors, installing adequate lighting in my home office (replaced incandescent bulbs for LED), new eyeglasses with lens specially designed for computer, etc because I was having terrible headaches 3 to 4 days a week. But I still am having them, I think my brain hates me (too).

> **coffeecat said:**
> 
One has Intel graphics, the other nvidia with the ppa 304.43 proprietary driver, both fully updated this morning. I've only checked firefox and the dash so far, but font rendering seems to be as good as it has been.


I'll keep a watch out in case it was an update that has caused your issue, and in case the update hasn't got to the update server I use.[/QUOTE]

> **VinDSL said:**
> I had this problem, a week or two ago.  Matter of fact, a lot of ppl were complaining about it, during the nVidia escapades.

At that time, I couldn't even log into Unity/GS, but the poor rendering quality was driving my eyes buggy in LXDE/Openbox.

Yea, it's making me mad :\ I have low degrees of astigmatism and myopia, it doesn't require thick glasses, etc. Normally If I force my eyes I can use the PC with no glasses at all. The way it is right now I'm unable to distinguish between dot vs comma and colon vs semi-colon. It makes my eyes useless for C++.
> **VinDSL said:**
> 
The "cure" in LXDE was to install a compositor. I chose XCompMgr, and the difference was jaw-dropping.

Haven't had a prob in Unity, so fiddling around with the compositing/compositor effects hasn't been required.


Just saying...

I tried to improve the situation using unsettings (or was it was gnome-tweak-tool, I can't remember) to change font faces/sizes. It made things worse and now I don't even remember what were Ubuntu defaults. 

You're probably right Vin, I was holding Unity updates before this problem. I have just updated, rebooted, purged/reinstalled X and Unity packages with no luck. I'll try to find the source for this later today. I never fiddled with fonts and rendering stuff, so I'm not sure what would be the packages, config files to play with. 

Regards,
Effenberg

---

### Post by Milos_SD on 2012-10-02
I have this problem too, mostly in firefox. It happend when I did this: sudo apt-get --purge remove libreoffice*. When that command finished what it had to do, fonts in firefox got ugly in the instant.

---

### Post by funicorn on 2012-10-02
xdpyinfo |grep resolution
cat /var/log/Xorg.0.log |grep DPI

see the outputs

---

### Post by Milos_SD on 2012-10-02
```
xdpyinfo |grep resolution
resolution:    96x96 dots per inch
```

```
cat /var/log/Xorg.0.log | grep DPI
[ 39622.629] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config

```

---

### Post by funicorn on 2012-10-02
What is your LCD screen size ?
and see output of
 ```
xpdyinfo |grep dimensions
```If your are sure that the display DPI is correctly used by Xserver. Next you should start to check in ~/.xsession-errors. It might be helpful if you don't mind posting the contents. 

Also,
```

declare -l lang=$(echo $LANG |awk -F [_.] '{print $1"-"$2}'); cat /etc/fonts/conf.d/69-language-selector-$lang.conf 

```would be helpful too.

> **Milos_SD said:**
> ```
xdpyinfo |grep resolution
resolution:    96x96 dots per inch
``````
cat /var/log/Xorg.0.log | grep DPI
[ 39622.629] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config

```

---

### Post by Milos_SD on 2012-10-02
> **funicorn said:**
> What is your LCD screen size ?
and see output of
 ```
xpdyinfo |grep dimensions
```If your are sure that the display DPI is correctly used by Xserver. Next you should start to check in ~/.xsession-errors. It might be helpful if you don't mind posting the contents. 

It is 23" DELL U2311H 1080p
```
xdpyinfo | grep dimensions
dimensions:    1920x1080 pixels (508x286 millimeters)
```

I think that before, in nvidia-settings it sad 96x95px or 95x94, can't remember, but it was defenetly not 96x96px, like it is now. I know this for sure, becouse I was wondering why it is like that. :)

Here is ~/.xsession-errors content: [http://pastebin.com/HW05hWev](http://pastebin.com/HW05hWev)

> 
Also,
```

declare -l lang=$(echo $LANG |awk -F [_.] '{print $1"-"$2}'); cat /etc/fonts/conf.d/69-language-selector-$lang.conf 

```would be helpful too.

This doesn't work. It says this:
```
cat: /etc/fonts/conf.d/69-language-selector-en-us.conf: No such file or directory
```

I have only this 69-language-selector-* files in that folder:

```
69-language-selector-ja-jp.conf  69-language-selector-zh-hk.conf  69-language-selector-zh-sg.conf
69-language-selector-zh-cn.conf  69-language-selector-zh-mo.conf  69-language-selector-zh-tw.conf
```

---

### Post by funicorn on 2012-10-02
Nothing looks wired except for this: Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected. 

check that file and see if anything looks wrong. It's may be related to your problem, and may be not. It seems to me there is some *fonts.conf in your system which overrides the default /etc/fonts/fonts.conf. Here is what you can do, 

1. Make sure following packages are normally installed:
fontconfig fontconfig-config libfontconfig1 libexpat1 libfreetype6 ttf-ubuntu-font-family ttf-dejavu-core fonts-freefont-ttf

2. ```
locate fonts.conf 
```find out all of the font conf files in your system, and to identify which might be responsible for the problem, i.e., which seems to be an alien creation.
you can run 'dpkg -L fontconfig-config' first to get the native installation list of font conf files.

3. check in  ~/.fonts.conf, ~/.config/fontconfig/fonts.conf and ~/.config/fontconfig/conf.d/*.conf,  in case there is anything wrong, i.e., font missing or using wrong font family.

4. generate a user font conf file if it's not there, which has highest priority, like this 
cat ~/.config/fontconfig/fonts.conf
> 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match>
    <test name="family"><string>sans-serif</string></test>
    <edit name="family" mode="prepend" binding="strong">
        <string>Ubuntu</string>
        <string>DejaVu Sans</string>
    </edit>
</match>
<match>
    <test name="family"><string>serif</string></test>
    <edit name="family" mode="prepend" binding="strong">
        <string>DejaVu Serif</string>
    </edit>
</match>
<match>
    <test name="family"><string>monospace</string></test>
    <edit name="family" mode="prepend" binding="strong">
        <string>Ubuntu Mono</string>
        <string>DejaVu Sans Mono</string>
    </edit>
</match>
</fontconfig>
5. If the problem still exists,  then do this: (Note: This is only for test. Delete these files when you find the real solution.)
```

mkdir -p ~/.config/fontconfig/conf.d/ && cd ~/.config/fontconfig/conf.d/
dpkg -L fontconfig-config |grep -E /etc/fonts/conf.d/.*conf |xargs cp -t .

```6. still no?
Then there's something wrong with xserver or the video driver. Try to file a bug on this.

---

### Post by WorLord on 2012-10-03
Create a new user.  Log in as the new user.  

Text still grainy?

---

### Post by Milos_SD on 2012-10-03
It is not grainy here. On some web sites it text is blurry, and on others numbers and text have some colors. Even the text when you hover over speed dial in firefox have that color to it. Not all characters have that, but I noticed that for "www" and "//". Including "" (it is like that here too). :S

---

