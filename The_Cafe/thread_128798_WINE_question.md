---
title: "WINE question"
date: 2006-02-12
forum: The Cafe
---

### Post by Fallen2 on 2006-02-12
Ok, I have just download WINE and installed it perfectly.  No how do I get programs to install with it?  Like for example just for the heck of it I tried to download IE 6 and then I tried to install it with WINE.  Well it says I can't because I don't have an internet connection.  What's wrong?  And when things do download when do they go?  thanks for your help.

---

### Post by Sutekh on 2006-02-12
First you need to run
```
winecfg
```
either from a terminal or by pressing **Alt**+**F2**

Once you run winecfg, and used it to setup options, you can install a program using **wine** and the location of the program executable (.exe)
```
wine /path/setup.exe
```
For example, running a setup program from the CD-ROM
```
wine /media/cdrom0/setup.exe
```
obviously it would be different depending on the program.

---

### Post by xequence on 2006-02-12
> Well it says I can't because I don't have an internet connection.

IE6 when you download it it is like 600KB. It then downloads and installs the rest when you open it...

And I think someone has a howto to get IE in wine. (Aysiu maybe? Poofy maybe? I think it was someone with alot of posts, but I dont remember)

---

