---
title: "Notepad++"
date: 2009-10-26
forum: Wine
---

### Post by zunebuggy on 2009-10-26
I am trying to install Notepad++ using Wine. I have tried downloading the zip, the exe and the 7z file.  When I try to install with wine, I get the following (I'm a total noob to ubuntu):

[/home/joe/.cache/.fr-8naaJy/unicode/notepad++.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/joe/.cache/.fr-8naaJy/unicode/notepad++.exe or
          /home/joe/.cache/.fr-8naaJy/unicode/notepad++.exe.zip, and cannot find /home/joe/.cache/.fr-8naaJy/unicode/notepad++.exe.ZIP, period.

---

### Post by vinutux on 2009-10-26
Y Notepad ++ Gedit is enough and more native.......

Check wineDB **[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13036&iTestingId=32680]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13036&iTestingId=32680")**

---

### Post by DoktorSeven on 2009-10-27
Installing and running it worked absolutely perfectly for me.  Download the *executable* version of N++ (npp.5.5.1.Installer.exe), place it in a known directory (in your home directory) and open a terminal (gnome-terminal for Ubuntu, konsole for Kubuntu, not sure what other variants use, just look for some sort of terminal program).

If you have it in the base of your home directory you should be fine, otherwise type **cd** followed by a space then the path where you saved the file.

Then simply type
**wine npp.5.5.1.Installer.exe**

The installer should start, you can go through it as usual, and it'll exit and optionally launch notepad++, and a shortcut should be added to your menu under Wine to it.  (If not, the "fake" Windows C drive is in ~/.wine/drive_c/ and the program is usually under Program Files/Notepad++ unless you changed it on install; you can just run the executable using Wine as you did with the installer.)

---

### Post by michaelzap on 2009-10-27
I really like Notepad++...on Windows. On Linux I usually use either Gedit or Geany. There are tons of other options also, such as Bluefish, Scite, etc. If you haven't tried native Linux text editors yet, you probably should give them a try. If you have and just decided that you prefer Notepad++, well then more power to you.

---

### Post by beastrace91 on 2009-10-27
One feature I really love about NP++ is the "clone to another view" tab feature - where is I can be viewing two different sections of the same file in a split screen mode. GEdit lacks this feature - anyone know if there is another Linux text editor that has it?

Also NP++ is open source right? I wonder why there isn't a Linux port yet... :O

~Jeff

---

### Post by alex.rayu on 2009-10-27
I fond linux to be quite rich for the editors like gedit, geany, bluefish, aptana, komodo edit, scream, now redcar editor coming out. To use the wine yoga just so you could tab copy...

---

### Post by zunebuggy on 2009-10-27
Thanks everyone.  I got it to work with: [B]wine npp.5.5.1.Installer.exe

[/B]I was using the top menu and selecting Applications > Wine > Browse... and getting that error.

---

### Post by vinutux on 2009-10-27
ok...plz....mark thread SOLVED

---

### Post by michaelzap on 2009-10-27
> **beastrace91 said:**
> One feature I really love about NP++ is the "clone to another view" tab feature - where is I can be viewing two different sections of the same file in a split screen mode. GEdit lacks this feature - anyone know if there is another Linux text editor that has it?

Something like this?
[http://eldapo.lembobrothers.com/2008/07/16/gedit-plugins-split-screen/](http://eldapo.lembobrothers.com/2008/07/16/gedit-plugins-split-screen/)

---

### Post by beastrace91 on 2009-10-27
> **michaelzap said:**
> Something like this?
[http://eldapo.lembobrothers.com/2008/07/16/gedit-plugins-split-screen/](http://eldapo.lembobrothers.com/2008/07/16/gedit-plugins-split-screen/)

Not exactly but close enough! Hehehe thank you :)

~Jeff

---

### Post by alex.rayu on 2009-10-27
Here's my last say.

[IMG]http://striderlance.com/repository/fun/spoil-wine-sm.jpg[/IMG]

---

### Post by vinutux on 2009-10-27
> **alex.rayu said:**
> Here's my last say.

[IMG]http://striderlance.com/repository/fun/spoil-wine-sm.jpg[/IMG]

wow....thatz cool....:D

---

### Post by RezaRM on 2010-12-16
And Why not GVIM?!

---

