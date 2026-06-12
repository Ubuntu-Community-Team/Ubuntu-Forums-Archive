---
title: "Will these bugs be fixed by release?"
date: 2018-04-07
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2018-04-07
There seems to be a pixel rounding bug on the screen edges for the panel that makes it not always clickable when the mouse it in the corner * see attached mp4 file
*seems on only affect the whiskers menu applet
[https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1764204](https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1764204)

[Fixed] This bug has had a patch for a while now:
[https://www.bountysource.com/issues/45489646-ristretto-fails-to-load-bmp-libmagic-gives-wrong-mime-type](https://www.bountysource.com/issues/45489646-ristretto-fails-to-load-bmp-libmagic-gives-wrong-mime-type)
My BIOS screenshots are in BMP format (only reason i have any images in this format)

[Fixed] It still hangs before the wallpaper appears, i recall seeing a thread here about it, it involved the bluetooth applet or something
this is far worse on my laptop then my desktop; then again my desktop does not have bluetooth hardware connected

---

### Post by kerry_s on 2018-04-07
it would be faster to just convert your bmp's than hoping for a fix.
```

mogrify -format jpg /path/to/your/bmps/*.bmp

```

i'm sure they will fix the hang/startup

you can help, make your voice heard, report those bugs. if only a few complain then whats the point of fixing if the rest don't care.

---

### Post by flocculant on 2018-04-08
> **pqwoerituytrueiwoq said:**
> There seems to be a pixel rounding bug on the screen edges for the panel that makes it not always clickable when the mouse it in the corner * see attached mp4 file
*seems on only affect the whiskers menu applet

This bug has had a patch for a while now:
[https://www.bountysource.com/issues/45489646-ristretto-fails-to-load-bmp-libmagic-gives-wrong-mime-type](https://www.bountysource.com/issues/45489646-ristretto-fails-to-load-bmp-libmagic-gives-wrong-mime-type)
My BIOS screenshots are in BMP format (only reason i have any images in this format)

It still hangs before the wallpaper appears, i recall seeing a thread here about it, it involved the bluetooth applet or something
this is far worse on my laptop then my desktop; then again my desktop does not have bluetooth hardware connected

Re the first issue : < ochosi> flocculant: not sure if that was ever fixed or even is fixable
                            < ochosi> flocculant: just looks like some signal mess with hover, maybe its fixed with the gtk3 panel already 

We'll not be doing the gtk3 panel for 18.04.

For the record - while I can reproduce, intermittently, this if I have a default panel. I have panel bottom left here so don't see it.

Re the second issue: can you report a bug there (or link to an existing one) will see if we can get that in, we're now in the bugfix only part of the cycle.

Final one - not sure what causes that - I do sometimes see it too, but very fleetingly. Again - bug report, though given where we are not sure it'll get dealt with now if it's not something simple.

---

### Post by pqwoerituytrueiwoq on 2018-04-08
> **flocculant said:**
> Re the second issue: can you report a bug there (or link to an existing one) will see if we can get that in, we're now in the bugfix only part of the cycle.
[https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242](https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242)

---

### Post by flocculant on 2018-04-09
> **pqwoerituytrueiwoq said:**
> [https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242](https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1762242)

thanks - passed along as

---

### Post by pqwoerituytrueiwoq on 2018-04-10
I found some threads referenced the 3ed issue
[https://ubuntuforums.org/showthread.php?t=2379455](https://ubuntuforums.org/showthread.php?t=2379455)
[https://ubuntuforums.org/showthread.php?t=2386737](https://ubuntuforums.org/showthread.php?t=2386737)

---

### Post by flocculant on 2018-04-11
New ristretto landed - please check that.

---

### Post by pqwoerituytrueiwoq on 2018-04-11
Did it make today's daily ISO?

---

### Post by mc4man on 2018-04-11
> **pqwoerituytrueiwoq said:**
> Did it make today's daily ISO?
You can always [ck. the .manifest file]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/"), then compare version to what you have or [URL="https://launchpad.net/ubuntu/+source/ristretto/0.8.2-1ubuntu1"]what's in launchpad

[/URL]

---

### Post by pqwoerituytrueiwoq on 2018-04-11
> **flocculant said:**
> New ristretto landed - please check that.
Yep, it worked

---

### Post by flocculant on 2018-04-12
> **pqwoerituytrueiwoq said:**
> Yep, it worked

Good - thanks for reporting, but most importantly perhaps - checking the fix works :p

---

### Post by pqwoerituytrueiwoq on 2018-04-15
> **flocculant said:**
> thanks - passed along as
Found another minor one xbm files do not open in it
[https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1764124](https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/1764124)

---

### Post by pqwoerituytrueiwoq on 2018-04-15
Reported the whiskers menu bug
[https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1764204](https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1764204)
* added to 1st port and marked fixed issues as such

---

