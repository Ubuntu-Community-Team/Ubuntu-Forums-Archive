---
title: "help with open office"
date: 2009-04-29
forum: The Cafe
---

### Post by roaddummy on 2009-04-29
Where do I install fonts for open office??  Thank you!!

---

### Post by meho_r on 2009-04-29
All fonts in your ~/.fonts directory as well as in /usr/share/fonts can be used in OpenOffice.org. Note that OpenType fonts are not supported in OpenOffice.org.

---

### Post by Priswell on 2009-04-29
I found this wiki very helpful:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Basically, you add fonts to the system, and then the programs, such as Open Office can find and use them. First use Synaptic to install msttcorefonts because they have a lot of the common Microsoft fonts, then add any other fonts to the fonts directory (I create another directory inside the fonts directory named "custom" so I can copy and move all of my specialty fonts from one computer to another easily). Anyway, the page noted above tells you how to do all that.

---

