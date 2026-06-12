---
title: "Arial Font in Office 2007"
date: 2009-12-06
forum: Wine
---

### Post by ownedbyhleb on 2009-12-06
I know this has probably been asked a million times, but I think my issue may be slightly different.

I install the windows core fonts package into wine, but when I used Office 2007, my arial font looks like this, which is awful, and nothing like what arial actually looks like...
[IMG]http://i49.tinypic.com/1jl1yv.png[/IMG]
[Click for big]("http://i48.tinypic.com/2m4atqa.jpg")

Is there are way to fix it? I have to write all my uni essays in arial so it would be much appreciated.

Thanks

---

### Post by ownedbyhleb on 2009-12-07
I have also tried doing this to no avail..
```
./winetricks corefonts

```

is there anyway to uninstall and re-install the fonts in wine?

---

### Post by dino99 on 2009-12-07
last good release: 1.1.28

---

### Post by ownedbyhleb on 2009-12-07
My arial fonts which are bold/bold italic display fine, but regular plain old arial doesn't..

1.1.28? Is that the version of wine i should be using? I'm currently using 1.1.14... how do I update?

Sorry for being a noob :(

---

### Post by Leighman on 2009-12-08
You could try the latest version of Wine by adding this PPA ([https://edge.launchpad.net/~ubuntu-wine/+archive/ppa](https://edge.launchpad.net/~ubuntu-wine/+archive/ppa)) to your Software sources then updating

---

### Post by ownedbyhleb on 2009-12-08
Managed to get the updated beta release of wine installed. However, my arial font's still look really dodgy, and are totally different spacing to that found in open office. Is there a fix for this or it as best as i'll get..

heres a comparison screenshot..
[IMG]http://i46.tinypic.com/2ldc13m.jpg[/IMG]
[Click for big]("http://i50.tinypic.com/35jmq1w.png")

---

### Post by RedVivi on 2010-04-11
I have exactly the same issue with the same font (Wine 1.1.42). Did anyone managed to fix it ?

Regards,
RedVivi

---

### Post by RedVivi on 2010-04-14
Am I the only one to get this bug ? :confused:

---

### Post by daqron on 2010-10-27
RedVivi: you are not the only one. This happens on every Ubuntu machine I try to install Office 2007 on. I have tried every solution posted anywhere on the entire internet and nothing works. I even tried removing every copy of Arial from my system and copying only one Arial.ttf font over from Windows and it still shows up bold and italic in Office. So frustrating.

**EDIT:** After painstakingly editing the binary code of every single file on my system by hand and inventing a new thing I like to call a "wheel" (it's gonna catch on) I think I have pinpointed the source of the problem:

I originally used PlayOnLinux to install Office 2007. It seems to have created two of its own fonts folders at: **~/.PlayOnLinux/fonts** and **~/.PlayOnLinux/wineprefix/Office2007/drive_c/windows/Fonts/**. I deleted everything with "Arial" in the name from both and this seems to have fixed the problem.

---

### Post by anil1010.it@gmail.com on 2011-03-06
Try this:
Remove font ariblk.ttf from /home/anil/.wine/dosdevices/c:/windows/Fonts

---

### Post by Humphreybas on 2011-04-11
My Arial font somehow allways displayed arial narrow (also quite ugly  and irritating). It said Arial in the menu bar but when I right  clicked->Font.. it said Arial Narrow and changing it didn't had any  effect.
Then I removed all the ARIALN*.ttf (arial narrow) files which worked!
It is a dirty workaround if you don't need Arial narrow.

ownedbyhleb you seem to have the exact same problem after updating wine  (second screenshot shows arial narrow when I'm not mistaking).

---

### Post by diegocarrera on 2012-02-02
The **sant527 **solution is 
"copy pasted the fonts from /usr/share/fonts/TTF to wine fonts folder."

I confirm it with office 2007, wine 1.2.3, on ubuntu 12.04

More info:
[https://bbs.archlinux.org/viewtopic.php?id=85931](https://bbs.archlinux.org/viewtopic.php?id=85931)

---

