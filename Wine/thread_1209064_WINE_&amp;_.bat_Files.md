---
title: "WINE &amp; .bat Files"
date: 2009-07-09
forum: Wine
---

### Post by TheSe7enthSin on 2009-07-09
Hey there, I was wondering if someone can help me out here.
I have a .bat file. I need to drag a specific file onto the .bat icon in order for it to compile. With Ubuntu, this doesn't work. How can I do this using WINE?

Is there a command I can enter using the Terminal that will give me the equivalent of the "Drag & drop" into the .bat?

---

### Post by synapsys on 2009-07-09
I don't understand your post?

What exactly are you trying to compile?

---

### Post by zerhacke on 2009-07-09
I heartily suggest compiling Windows programs on a Windows computer.

---

### Post by TheSe7enthSin on 2009-07-09
> **zerhacke said:**
> I heartily suggest compiling Windows programs on a Windows computer.

Will it do harm to the Linux machine or is it just a waste of time?

I have some homebrew Palm Pre apps that I am trying to install on the phone. I need to drag the app file onto a specific .bat file.

---

### Post by zerhacke on 2009-07-09
It won't hurt to compile a Windows program on Linux, but Linux can't run Windows programs so you won't be able to use the programs (yes I know about WINE).

The thing is, cross compiling for a Palm application with a Windows compatibility layer on Linux... it's just easier and less problematic to do these things on the intended platform.

---

### Post by Elep.Repu on 2009-07-09
> **zerhacke said:**
> It won't hurt to compile a Windows program on Linux, but Linux can't run Windows programs so you won't be able to use the programs (yes I know about WINE).

The thing is, cross compiling for a Palm application with a Windows compatibility layer on Linux... it's just easier and less problematic to do these things on the intended platform.

And faster probably.

---

### Post by SaxMeister13 on 2009-07-09
I just did some work with Palm OS a couple of weeks ago using batch files.  The trick is to run them from the terminal using Wine's impression of CMD from Windows.  As far as the drag-and-drop, though...maybe you could make another batch file that runs the first one using the file as a parameter? :-s

---

### Post by lavinog on 2009-07-09
As far as I remember draging a file to a bat file is the same as running the bat file from the command line with the file as an argument
in which case compiling your palm app should work with wine. You can help the wine community out by posting your results on the wine appdb [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

What program are you using to compile the palm app?
There is likely to be a palm compiler for linux

---

### Post by lavinog on 2009-07-09
> **Elep.Repu said:**
> And faster probably.

Sometimes running apps in wine is faster, and less problematic
ex: moo2 runs in wine (although there is a regression with menus currently) while I cannot get moo2 to work on winxp sp3 or vista.

---

