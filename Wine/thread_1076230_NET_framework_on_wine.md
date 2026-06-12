---
title: "NET framework on wine?"
date: 2009-02-21
forum: Wine
---

### Post by StOoZ on 2009-02-21
I have an app which requires to have the net framework to run , is it possible somehow?

---

### Post by GARoss on 2009-02-21
No.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586)

---

### Post by kestrel1 on 2009-02-21
What is the app?
Have you thought of running VirtualBox & running Windows on it.

---

### Post by ajackson on 2009-02-21
If you use winetricks ( [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) ) you should be able to get .NET 1.1 & 2.0 installed. From there it is a case of try the app and see what happens, somethings will work and some won't.

---

### Post by Sprut1 on 2009-02-21
What application is this? There might be a similar Linux application :)

---

### Post by Cilionelle on 2009-02-23
Hey there.  How do I get the wine tricks script to work?  I've never done this before in my life and I too need Wine to work nicely with a .NET application (the D&D Character Builder, of which there is no specific Linux build... nice try tho!).  cheers!

---

### Post by konqueror7 on 2009-02-23
> **kestrel1 said:**
> What is the app?
Have you thought of running VirtualBox & running Windows on it.

+1, better use vbox...

---

### Post by ajackson on 2009-02-23
Easiest way to get winetricks working is via the terminal

```
wget http://kegel.com/wine/winetricks
```
To fetch the script and
```
chmod +x winetricks
```
to make it executable, then just
```
./winetricks
```
makes it pop up a window showing the stuff it can install, find dotnet11/dotnet2, tick whichever is needed and click OK.

---

### Post by wolfyking2 on 2009-02-23
I think I needed .Net 3.0 for this spring engine mabobber, and it just installed automatically.  But it might be something different, so I'm not sure.

---

### Post by bbynum on 2010-03-27
> **ajackson said:**
> Easiest way to get winetricks working is via the terminal

```
wget http://kegel.com/wine/winetricks
```To fetch the script and
```
chmod +x winetricks
```to make it executable, then just
```
./winetricks
```makes it pop up a window showing the stuff it can install, find dotnet11/dotnet2, tick whichever is needed and click OK.



I really hopes this work..I am new to Ubuntu and easily find myself getting frustrated. All in all I like Linux/Ubuntu much better than Windows, but it gets a bit frustrating when everything that I normally navigate needs this or needs that to run. Working 16 hours a day the last thing I want to do is have to program a pc...lol..I am trying not to give up on Ubuntu just yet because in the end I know I will be happy with the end result.. Wish me luck!

---

### Post by asdfoo on 2010-03-27
> **bbynum said:**
> I really hopes this work..I am new to Ubuntu and easily find myself getting frustrated. All in all I like Linux/Ubuntu much better than Windows, but it gets a bit frustrating when everything that I normally navigate needs this or needs that to run. Working 16 hours a day the last thing I want to do is have to program a pc...lol..I am trying not to give up on Ubuntu just yet because in the end I know I will be happy with the end result.. Wish me luck!

no one is holding a gun to your head...   I use Wine for fun in my spare time, but if I have none I just use Vista.

---

### Post by Iksf on 2010-08-21
Mono is by far your best bet

---

### Post by harvodan on 2010-08-22
Winetricks now supports up to dotnet 3.0, though I cannot guarantee that the app in question will work, it's still worth a shot. Mono under wine or natively doesn't quite seem to do the job as far as I've seen, but you never know.

with any script, which is what winetricks is, you can just select the file, right-click, go to properties, select Permissions, and check the "Execute file as program" box. Also, under ubuntu with the wine ppa, you can install winetricks through synaptic package manager, under System> Administration.

---

