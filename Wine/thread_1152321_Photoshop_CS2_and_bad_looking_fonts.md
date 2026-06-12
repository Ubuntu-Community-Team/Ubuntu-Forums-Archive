---
title: "Photoshop CS2 and bad looking fonts"
date: 2009-05-07
forum: Wine
---

### Post by alexandari on 2009-05-07
Hello there. I`m running Kubuntu 9.4. I installed photoshop cs2 using the latest version of wine and when I launched it,the fonts were looking...bad
you`ll see what I`m talking about ---> [[IMG]http://img217.imageshack.us/img217/7729/thefuck.th.png[/IMG]](http://img217.imageshack.us/my.php?image=thefuck.png)

I did **sudo apt-get install msttcorefonts**
I did  **wget [http://kegel.com/wine/winetricks;](http://kegel.com/wine/winetricks;) sh winetricks corefonts vcrun6**
and that`s all... any ideas? :KS

---

### Post by alex.rayu on 2009-05-08
My idea is that it's thanks to compiz.

---

### Post by alexandari on 2009-05-08
I`m not using compiz or any desktop effects

---

### Post by alexandari on 2009-05-08
bumpy wumpy

---

### Post by FredDie3785 on 2009-08-01
Thread is a little bit old, but I've got the same problem. Just like the author of this topic, I'm not using compiz or any other desktop effects. Any solution?

---

### Post by FredDie3785 on 2009-08-01
Ok, few looks through the [magic googles]("http://www.google.com") and I've found the solution. You need to download the **Tahoma** font. 
For example from here:
[http://cid-a69c4d1ba0c53559.skydrive.live.com/self.aspx/WinExperience/Fontes/TAHOMA.TTF]("http://cid-a69c4d1ba0c53559.skydrive.live.com/self.aspx/WinExperience/Fontes/TAHOMA.TTF")
Then just copy file to /home/<user>/.wine/drive_c/windows/fonts/
Now I don't have screwed fonts.

Cheers...

---

### Post by alexandari on 2009-08-01
I found out the solution but forgot to tell you. It`s pretty simple...it`s even stupid.
You just need to change the font size in photoshop. It`s somewhere in the options I cant tell you right now I dont have it installed :< It`s set to "small" by default. Dont know why

---

### Post by alex.rayu on 2009-08-01
Compiz rehabilitated then. Posthumously.

---

