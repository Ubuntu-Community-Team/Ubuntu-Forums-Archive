---
title: "How to install Wine"
date: 2009-05-03
forum: Wine
---

### Post by GreenBowlPacker_3 on 2009-05-03
I downloaded Wine from winehq.org and tried installing it using
```
sudo apt-get update
sudo apt-get install wine
sudo apt get install winesetuptk
```

I keep getting an error message.  What am i doing wrong?

---

### Post by akoskm on 2009-05-03
> **GreenBowlPacker_3 said:**
> I downloaded Wine from winehq.org and tried installing it using
```
sudo apt-get update
sudo apt-get install wine
sudo apt get install winesetuptk
```

I keep getting an error message.  What am i doing wrong?

What is the error message?
Why don't you install it from synaptic?

---

### Post by GreenBowlPacker_3 on 2009-05-03
This is the error message.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

```

How do I install it with synaptic?

---

### Post by akoskm on 2009-05-03
Open System > Administration > Synaptic Package Manager.
Here type into the Quick search field: wine.
From the listed packages right click to *wine* and *wine-gecko* and select Mark for Installation. Apply.
Hope that helps.

---

### Post by GreenBowlPacker_3 on 2009-05-03
I tried searching but nothing came up when I searched for wine.

---

### Post by tacantara on 2009-05-03
Wine and Wine-gecko are listed in Synaptic.  The problem is that it downloads Version 1.0.1 by default.  The current (development) version available for release is 1.1.20.  Supposedly, the development release offers more compatibility than the "stable" 1.0.1 version, and you have to download the .tar.bz2 file from their website (winehq.org).  Once you download it, you have to extract the files and install.  I attempted this earlier today, and had to scrap the process because I received error messages that I could not resolve through searching the forums.

If you are looking to run MS programs that do not have a Linux equivalent (i.e. Zune software), you're better off downloading Sun's VirtualBox and setting up a Windows virtual machine.  JMHO.  I did that, and the process went much smoother.  VirtualBox even allows the virtual machine to access your computer's hardware (CD/DVD, USB, etc.).

---

### Post by hesperus on 2009-05-03
Have you tried these instructions:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by GreenBowlPacker_3 on 2009-05-03
> **hesperus said:**
> Have you tried these instructions:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Yes, and that wasn't much help.

---

### Post by hesperus on 2009-05-03
What do you get when try the command line:

Try:

[I]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Followed by:

[/I][I]sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list

Post the output. It looks like you haven't installed the repository correctly hence why the wine package can't be found
[/I]

---

### Post by hesperus on 2009-05-03
watch out as the second url has been foreshortened

---

### Post by tacantara on 2009-05-03
After taking a break and thinking it out, I came to the same conclusion as hesperus, and went to [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") and followed the instructions.  By following the instructions (plus opening the Update Manager and seeking out the most recent development package) I was able to successfully install Wine.

---

### Post by dino99 on 2009-05-03
hi,

just my 2 cents :P

don't know what you want with wine, but if you glance at stability, choose wine from synaptic, the others are not stable.
Then find winetricks and install first all the fonts and codecs: only that first if you don't want to fall in trouble :lolflag:

( you can find it with google: "ubuntu winetricks"), it's a script and you don't need to install it, simply type 'winetricks'in the terminal.

Close wine when done, then open it again and install what you want or need.

:popcorn:

---

### Post by Mr. Hibba on 2009-05-04
If you can't find WINE in the Synaptic manager, you need to make sure that your filter at the top says "All Open-Source Software" (not sure if I got it exactly right). It should come up in the searches.

As tacantara said, it doesn't download the developmental packages "by default." (Quoting tacantara at the end there. I didn't feel right taking her words :) ) 
  Mr. Hibba.

---

