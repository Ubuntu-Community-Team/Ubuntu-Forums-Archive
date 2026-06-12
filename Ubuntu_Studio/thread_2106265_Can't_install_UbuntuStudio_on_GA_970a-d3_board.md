---
title: "Can't install UbuntuStudio on GA 970a-d3 board"
date: 2013-01-18
forum: Ubuntu Studio
---

### Post by edgebuntu on 2013-01-18
Hi everyone,
I been trying to install Ubuntu Studio 12.04 in a new PC, but after selecting the lenguage it tries to load the installer but instead it loads the Ubuntu Studio Desktop image, then the  screen goes black and it tries to load but nothing, then the mouse cursor appears as an X and thats all.

I also tried to install Ubuntu 12.04 but at some point it gives me an error, telling that it may be the CD/DVD unit or the an error in CD, but i tested em in other PC's and they are ok :(

The board i have is a Gigabyte 970A-D3 rev. 1.3 a AMD FX-8150 processor and the video card is a ZOGIS Nvidia Geoforce GT 610.

---

### Post by Sylos on 2013-01-19
Have you tried booting with the no "nomodeset" parameter? That normally sorts out issues with getting black screens.

Cheers

EDIT: That issue you are having with the vanilla Ubuntu install sounds familiar to me. I think I had a similar message when the Lubuntu installer kept crashing. It turned out to be down to the slideshow that comes up. You could try booting the disk into the "try ubuntu..." option, open a terminal then type:

```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

That may then allow you to get through the installation process.

Cheers

---

### Post by edgebuntu on 2013-01-22
i'm gonna try it, hope it works, thanks for the help

---

### Post by edgebuntu on 2013-01-29
At the end i ended up installing the HDD in another computer and istalling the Ubuntu Studio and reinstalling it back into my PC and it worked, now the question is what was the problem? Drivers, the NVidia Card? I really dunno... :-s

---

