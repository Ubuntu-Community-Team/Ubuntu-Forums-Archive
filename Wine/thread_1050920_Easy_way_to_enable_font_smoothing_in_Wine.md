---
title: "Easy way to enable font smoothing in Wine"
date: 2009-01-26
forum: Wine
---

### Post by TiGR on 2009-01-26
As most of you already know, wine supports font smoothing, including subpixel since wine 1.1.12. The problem is, this feature is disabled by default. There are many advices in internet on how to enable it (which includes working out with registry etc).

But I've thought that enabling and configuring such thing as font smoothing should not require any registry work. So, I've written [a script](http://files.polosatus.ru/winefontssmoothing_en.sh) that does all the job for you:

[IMG]http://www.picamatic.com/show/2009/01/26/03/50/1868127_470x280.png[/IMG]

Quick way to run it:```
wget http://files.polosatus.ru/winefontssmoothing_en.sh
bash winefontssmoothing_en.sh
```
Enjoy :)

---

### Post by NeferalCrossfireX on 2009-02-23
Works perfectly thanks^^

now i have ubuntu wine colours and smoothed fonts:guitar:

---

### Post by binbash on 2009-02-24
Works perfect ;)

---

### Post by yeats on 2009-03-10
Thanks so much - this was a simple solution to a really annoying problem that I've just been living with. =D>

---

### Post by alex.rayu on 2009-03-10
Excellent!

---

### Post by radtek on 2009-03-11
It appears to have worked but I'm not sure to what effect.

Could someone please post some screenshots of before and after?

Thanks...

---

### Post by TiGR on 2009-03-11
Here it is. These samples taken in winecfg, graphics tab, there at the bottom you can select dpi, and see big text. First is no smoothing, second - grayscale, third - RGB subpixel.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=106118&d=1236797572[/IMG]

---

### Post by ffi on 2009-03-26
For some reason only 6,7 and 8 point fonts are smoothed. Anyway to turn this on for all fonts?

---

### Post by TiGR on 2009-03-26
That's not correct. All font sizes are being smoothed. The exception is made for fonts that have built-in bitmap fonts. If font has one, wine would use it, and it won't be smoothed.

---

### Post by ffi on 2009-03-26
but this is what's happening, anyway to correct this?

---

### Post by starcannon on 2009-03-26
Sweet, thank you very much.

---

### Post by dakaujunk on 2009-08-22
Somehow, this smoothing option does not seem to work with DPIs less than 120 :( I know this thread is old, but would anyone know why?

---

### Post by TiGR on 2009-08-23
Smoothing for windows fonts in wine works only for fonts larger than ~ 14 pt, since wine uses another rendering technique for small windows fonts. Thus, you can see font smoothing in wine only on larger windows fonts or on custom fonts.

---

### Post by Leoncio on 2009-09-29
Awesome!  Thanks a bunch!

---

### Post by Rayaz on 2010-03-27
You made my day, thanks a ton!:popcorn:

---

### Post by gianninardoia on 2010-04-27
> **TiGR said:**
> As most of you already know, wine supports font smoothing, including subpixel since wine 1.1.12. The problem is, this feature is disabled by default. There are many advices in internet on how to enable it (which includes working out with registry etc).

But I've thought that enabling and configuring such thing as font smoothing should not require any registry work. So, I've written [a script]("http://files.polosatus.ru/winefontssmoothing_en.sh") that does all the job for you:

[IMG]http://www.picamatic.com/show/2009/01/26/03/50/1868127_470x280.png[/IMG]

Quick way to run it:```
wget http://files.polosatus.ru/winefontssmoothing_en.sh
bash winefontssmoothing_en.sh
```Enjoy :)


hello,
the script is not available... can you help me?
thank you.

---

### Post by v1ad on 2010-04-27
yea cant download the script

---

### Post by Steam. on 2010-04-27
I also want a reupload.

---

### Post by dino99 on 2010-04-28
if any body want an uptodated and trusted script, look at winetricks, it does a wide nice job.

---

### Post by maxsocial on 2010-05-06
Thank you! It works like a charm!

---

### Post by TiGR on 2010-05-06
Sorry for the downtime, my site was down for a while, now everything should be back to normal again.

---

### Post by PeterRJG on 2010-05-07
Thanks for this. Works like a charm.

---

### Post by cbrunhaver on 2010-05-20
Thanks you!  This worked perfectly.

---

### Post by Nicram on 2010-07-31
At last!
After years of searching! :)

Thank you!

---

### Post by Uruz on 2010-08-23
Is the site down again? I can't get it.

**EDIT**
Nevermind, Problem solved.

---

### Post by marl30 on 2010-08-24
I get far better results using Winetricks than this method.

---

### Post by thort on 2010-08-26
Thank You! :)

---

### Post by nh7o_hi on 2010-10-20
Excellent. Thanks very much!

---

### Post by paul1149 on 2012-07-11
Thank you, TiGR!! Awesome.

---

