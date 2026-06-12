---
title: "remove ubuntu studio fonts"
date: 2014-09-18
forum: Ubuntu Studio
---

### Post by tarunperkins on 2014-09-18
Hi all. I'm running Ubuntu Studio 14.04 and I'm truly shocked (and a bit disgusted) by the amount of fonts that came with it. I know that I could go through the list in font manager and disable the ones I don't like, but it really would take *forever*, and 9 out of 10 of them are distasteful to me. Can anyone recommend some meta packages to uninstall, or guide me through restoring a more typical, default core of ubuntu fonts?

---

### Post by ibjsb4 on 2014-09-18
Most fonts are kept in /usr/share/fonts

---

### Post by vasa1 on 2014-09-18
You could try looking at 
```
dpkg --get-selections | grep "font" > ~/Desktop/fonts.txt
```
and then running **sudo apt-get purge *font-name*** where font-name is what you find "shocking" or "distasteful" or "disgusting" or whatever.

This is what my fonts.txt looks like

```
fontconfig					install
fontconfig-config				install
fonts-dejavu-core				install
fonts-droid					install
fonts-freefont-ttf				install
fonts-liberation				install
fonts-opensymbol				install
gsfonts						install
libfontconfig1:amd64				install
libfontconfig1-dev				install
libfontembed1:amd64				install
libfontenc1:amd64				install
libxfont1:amd64					install
ttf-ubuntu-font-family				install
xfonts-base					install
xfonts-encodings				install
xfonts-mathml					install
xfonts-utils					install
```

---

### Post by nova-deviator on 2014-09-20
I would totally agree with that. There should be some quality selection of fonts. As it is now, it seems like every possible free/gpl font has been added. It really is so many of them, that one cannot even go through them using font manager and disable them... uninstalling them in a way suggested above is also quite tedious as you cannot preview them while uninstalling them.

---

### Post by jejeman on 2014-09-20
You are welcome to join the project and do the quality font selection, etc.

---

### Post by bhilmers2 on 2015-05-27
> **jejeman said:**
> You are welcome to join the project and do the quality font selection, etc.I would love too. How do I join the project? The font situation is out of control. There are waaaaaay to many fonts installed and >90% are either impractical or novelty typefaces. As a professional designer this is one of the big disappointments in Ubuntu Studio and why I keep going back and forth between this distro and Mint. Managing so many fonts is a big hassle, especially considering I use my own library and almost never use any of the pre-installed ones.

---

### Post by jejeman on 2015-05-28
Check this
[https://ubuntustudio.org/contribute/](https://ubuntustudio.org/contribute/)
and this
[http://ubuntuforums.org/showthread.php?t=1124138](http://ubuntuforums.org/showthread.php?t=1124138)

---

