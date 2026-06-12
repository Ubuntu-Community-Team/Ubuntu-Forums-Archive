---
title: "Problem in Wine with Russian Fonts or Codepages"
date: 2010-05-27
forum: Wine
---

### Post by vovuntu on 2010-05-27
While trying to run a program in Wine , I encountered a problem with russian alphabet. There are 2 scenarios:

**1.** when I start the program in such a way:
         wine start run.bat
it displays the charcters in that way
[[IMG]http://img268.imageshack.us/img268/7767/screenshotgs.th.png[/IMG]](http://img268.imageshack.us/i/screenshotgs.png/)


[[IMG]http://img241.imageshack.us/img241/9264/screenshot1ih.th.png[/IMG]](http://img241.imageshack.us/i/screenshot1ih.png/)



[[IMG]http://img443.imageshack.us/img443/8637/screenshot2vd.th.png[/IMG]](http://img443.imageshack.us/i/screenshot2vd.png/)



as you see the program is using pseudo-graphics...


**2.**when I start the program in such a way:
       LANG=ru_RU.CP1251 wine start run.bat
       [as far as I understand using the RU locale] 
This is what I got:
[[IMG]http://img28.imageshack.us/img28/6466/screenshot3q.th.png[/IMG]](http://img28.imageshack.us/i/screenshot3q.png/)


[[IMG]http://img338.imageshack.us/img338/999/screenshot4mw.th.png[/IMG]](http://img338.imageshack.us/i/screenshot4mw.png/)


As you can see, now it's the Cyrillic alphabet, but also someproblem persists...

in both cases in the Terminal is displayed the following error:
:WineEngCreateFontInstance Untranslated charset 255
May that could help in solving the problem...
Viewfull/
What I have already done:
1. Copied the Windows fonts in the Wine's Fonts folder[Windows/Fonts]
2. Generated the locales for RU
3. Copied the fonts in /usr/share/fonts
And as you see  - No Results!



Please help me solving it!!!

---

### Post by cogadh on 2010-05-27
Um, I don't see any examples, just blank spaces where examples should be.

---

### Post by vovuntu on 2010-05-28
Try to click on that blank spaces..

---

### Post by cogadh on 2010-05-28
Yeah, I already did that, there is nothing there at all to see or click. I even tried highlighting all the text of your post, there isn't even a placeholder for something, it is literally just blank space.

---

### Post by vovuntu on 2010-05-31
EDITED!!Sorry ...

---

### Post by vovuntu on 2010-06-08
Help!!!

---

