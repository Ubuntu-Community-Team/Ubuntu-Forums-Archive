---
title: "Imagemagick convert seg fault - workaround?"
date: 2010-03-16
forum: Ubuntu Studio
---

### Post by BkkBonanza on 2010-03-16
Hello,
The current version of Imagemagick convert in Ubuntu 9.10 gives me a seg fault when trying to convert multiple jpg to a single pdf file. This used to work fine for me and looking in the bug database I see that this version 6.5.1.0 indeed has a seg fault bug reported. 

I'd like to somehow upgrade Imagemagick to use the package from Karmic. Does anyone know how to easily do this or maybe found a workaround for the bug? I tried the use Synaptics to "force package version" but that option is always grayed out. Maybe I can find the correct deb and manually install it?

Thanks for any help.

---

### Post by kaibob on 2010-03-16
> **BkkBonaza said:**
> Hello,
The current version of Imagemagick convert in Ubuntu 9.10 gives me a seg fault when trying to convert multiple jpg to a single pdf file.... I'd like to somehow upgrade Imagemagick to use the package from Karmic.Does anyone know how to easily do this or maybe found a workaround for the bug? 
I experienced the same issue in both Jaunty and Karmic. For me, the solution was to use graphicsmagick, which is in the repo's and is a very small install. The commands are pretty much the same except that you begin the command line with a "gm". 

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

BTW, you say that you experience the seg fault with the version of Imagemagick in Ubuntu 9.10 and you then state that you want to upgrade Imagemagick to use the package from Karmic. Do you mean the version in Lucid?

---

### Post by BkkBonanza on 2010-03-17
Thanks for the info.
I did mean Lucid.
I went looking through the packages web site and did find both graphicsmagick and the newer version of imagemagick. In the end I just downloaded and manually installed the newer 6.5.7 imagemagick packages and this worked ok for me.
This fixed the seg fault but after hours of messing around I still couldn't get satisfactory results with imagemagick. I used to be able to do this but for some reason these particular images gave me trouble and I couldn't get decent resolution conversions into pdf. The sources look great but the pdf looks like crap.

---

