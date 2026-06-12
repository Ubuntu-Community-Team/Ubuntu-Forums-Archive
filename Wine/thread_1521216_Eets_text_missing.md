---
title: "Eets text missing"
date: 2010-06-30
forum: Wine
---

### Post by woop12 on 2010-06-30
Hi.

 I'm trying to get the game "Eets" to run in wine ([http://www.eetsgame.com/news/index.php](http://www.eetsgame.com/news/index.php)). According to the wine AppDB it should work ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=8740&iTestingId=51240](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8740&iTestingId=51240)). 
It installed and started fine for me, however all the text is missing.

Are there some fonts that i maybe need to install or something like this?

Thanks in advance,
woop

//edit: if i disable Pixel Shader in winecfg i get come colored boxes where the text should be, instead of nothing

---

### Post by asdfoo on 2010-06-30
are you using the latest version of Wine? open a terminal and type 'wine --version' it should print wine-1.2-rc5.

do you have the latest drivers for your video card?

---

### Post by cogadh on 2010-06-30
Try using [winetricks]("http://wiki.winehq.org/winetricks") to install the MS core fonts.

---

### Post by woop12 on 2010-07-01
MS core fonts are installed. from the looks of it Eets uses its own fonts (in ttf) anyway.
wine version is 1.1.42
this is the newest version in the ubuntu repositories.

---

### Post by cogadh on 2010-07-01
But it is not the newest version. Go here for instuctions on getting the newest Ubuntu packages for Wine:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by woop12 on 2010-07-02
updated wine to wine-1.2-rc5, but the problem remains the same

---

