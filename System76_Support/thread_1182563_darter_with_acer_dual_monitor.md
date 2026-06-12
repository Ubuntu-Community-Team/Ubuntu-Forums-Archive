---
title: "darter with acer dual monitor"
date: 2009-06-09
forum: System76 Support
---

### Post by tessk on 2009-06-09
Hi ... hoping someone can help me with getting my Acer AL2216W monitor working with the Darter please.

This is what I've tried so far:

[LIST]
[*]I plugged it in and nothing happened
[*]So I went to Preferences > Display and tried different settings to no avail
[*]Then I tried adding the following to my /etc/X11/xorg.conf
[/LIST]
```
Section "Monitor"
        Identifier      "Acer AL2216W"
        VendorName      "Acer"
        ModelName       "AL2216W"
        HorizSync       31-101
        VertRefresh     60-160
        ModeLine "1680x1050_60.00"      147.14  1680    1784    1968    2256    1050    1051  $
EndSection

```
[LIST]
[*]After saving that file, I restarted the system, and much to my delight the second monitor mirrored the Darter's ... right up until the desktop appeared, at which point the second monitor just turned and stayed black
[*]To see if it was my changes to xorg.conf that caused the mirroring, I reverted the file, restarted, and it still mirrored, so probably that behaviour was already there
[/LIST]
Not sure where to go with this now! Advice much appreciated!

tess

---

### Post by thomasaaron on 2009-06-09
Does Display Preferences detect your external monitor? You should see two rectangles, one for your LCD and one for the external monitor.

If it does see it, does it detect the refresh rate and give you resolution options?

Also, do you get the same results with desktop effects disabled? (System > Prefs > Appearance > Visual Effects > None)

---

### Post by tessk on 2009-06-09
> Does Display Preferences detect your external monitor? You should see two rectangles, one for your LCD and one for the external monitor.Yes it does. See attached screenshot.

> If it does see it, does it detect the refresh rate and give you resolution options?As you can see in the screenshot it defaults to 1280x800 res and 60Hz refresh rate. There are other resolution options. Under the default resolution it only allows the 60Hz rate, but under other resolutions it gives the option of higher refresh rates.

> Also, do you get the same results with desktop effects disabled? (System > Prefs > Appearance > Visual Effects > None)My effects were already set to None. I just tried switching to Normal to see what would happen, and it did the same behaviour on a restart (mirror until desktop appeared).

Thanks for your help. I've gotta go to work now so I won't be able to try anything more until this evening.

---

### Post by PatrickVogeli on 2009-06-09
you could try to put the Acer display Abow or Below the laptop's one, which could make the trick. I know intel used to have problems and limited the desktop to 2048x2048

---

### Post by tessk on 2009-06-09
hmm pretty sure i tried putting it above at one point, but i'll try again later when i'm home, and let you know. thanks :)

---

### Post by thomasaaron on 2009-06-09
CLICK on the rectangle representing your external monitor. Then set it's resolution. Then click Apply.

---

### Post by tessk on 2009-06-09
that sounds deliciously easy ... will let you know how it goes in a few hours
 
thanks!!

---

### Post by tessk on 2009-06-09
well tried both patrick's and tom's suggestions and no luck unfortunately :( still mirrors when booting up then goes blank once the desktop appears

any other ideas?

if it helps, my xorg.conf currently looks like this (removed comments):

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2960 1050
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc104"
    Option "XkbLayout" "dvorak"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```

---

### Post by tessk on 2009-06-09
every time i try to configure the second monitor, i have to click the 'on' button. i apply the changes and restart, but when i go back into the display preferences, the monitor is set back to 'off' again.

---

### Post by thomasaaron on 2009-06-10
What if you just log out and back in, as opposed to restarting?

---

### Post by tessk on 2009-06-10
aha got it working! while i had played around with the resolution when i first started troubleshooting this, i didn't realize i had only been adjusting the darter's resolution. it turns out i had to adjust the acer's resolution - it doesn't work when it's on the default (highest) setting. so once i changed that, it worked.

thanks for everyone's input :)

---

