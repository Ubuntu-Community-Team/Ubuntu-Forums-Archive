---
title: "PeaZip 2.3a released"
date: 2008-09-24
forum: The Cafe
---

### Post by Giorgio tani on 2008-09-24
The new release contains Czech, English, German, Italian, Portugues and Russian localizations, thanks to users that contributed a translation.
Full changelog and download page on [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

---

### Post by Polygon on 2008-09-24
still has the 'font is too big for comboboxes' so once again a ton of people will not run this program, as its almost impossible to use if you cant read what the comboboxes say.

---

### Post by Giorgio tani on 2008-09-26
> **Polygon said:**
> still has the 'font is too big for comboboxes'
You are right, but in latest revision of the compiler I'm testing the problem of fixed (21px) combobox height seem resolved.
If all is ok as it seems (and I hope) PeaZip 2.3b for Linux will have higher comboboxes; 26 seems a widely agreed value on Gnome applications, but I'll do some more specific test with Debian and Ubuntu fonts).
In future I could consider also to make it a parametrizable variable that could be changed in theming panel.

---

### Post by Giorgio tani on 2008-10-20
PeaZip was included in Lifehacker's poll of best five compression tools (where obviously 7-Zip and WinRAR wins hands down), IMHO nice article:
[http://lifehacker.com/5065324/five-best-file-compression-tools](http://lifehacker.com/5065324/five-best-file-compression-tools)

---

### Post by Chame_Wizard on 2008-10-20
i hope it's good (7ZIp and ARK in Kubuntu:()

---

### Post by Disreali on 2008-10-30
I just installed PeaZip and I really want to like it. My main issue is that as soon as I open peazip it eats up the entire swap and my system stutters until I kill PeaZip. 
My system is fairly new and powerful. Acer M5620 with an Intel Core2 Q6600 @ 2.4GHz, 4GB ram, and 500GB HDD.  

Has anyone else found peazip to be a resource hog?  I have not used peazip on winbloz, so i don't know yet if it acts the same way in a different os.

---

### Post by FuturePilot on 2008-10-30
> **Disreali said:**
> I just installed PeaZip and I really want to like it. My main issue is that as soon as I open peazip it eats up the entire swap and my system stutters until I kill PeaZip. 
My system is fairly new and powerful. Acer M5620 with an Intel Core2 Q6600 @ 2.4GHz, 4GB ram, and 500GB HDD.  

Has anyone else found peazip to be a resource hog?  I have not used peazip on winbloz, so i don't know yet if it acts the same way in a different os.

Yes, it seems to want to eat my CPU every time I run it. :(

---

### Post by Giorgio tani on 2008-11-04
> **Disreali said:**
> Has anyone else found peazip to be a resource hog?
I usually test it on virtual Linux boxes (quite resource limited) and on an old notebook (older distributions) but I've never encountered similar performance problems in my tests.

Some functions, however, as system benchmark or some extreme compression settings (PAQ, higher 7Z and ARC compression settings), are meant to use a big amount of RAM and will use as much CPU as it is available.

Otherwise, if it happens without performing extremely heavy tasks, I can only think to some problems with machine's configuration I have not yet tested (or I was not able to replicate) on my test machines.
If you can specify further what happens, and the machine configuration, I can try to replicate it as close as possible to try to understand why the application fails to behave as expected.

BTW, next week it will be released 2.4 version, compiled with newer long term Lazarus IDE release, 0.9.26.
This new version will have larger (and customizable) comboboxes to fit the default Ubuntu font size, fixing the issue about option's readability on Ubuntu systems previously reported in this forum.

---

