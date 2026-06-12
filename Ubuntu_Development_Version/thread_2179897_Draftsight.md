---
title: "Draftsight"
date: 2013-10-10
forum: Ubuntu Development Version
---

### Post by Smask on 2013-10-10
Happy happy - Joy joy!

I don't need to run 32bit raring any more.

---

### Post by gspe on 2013-10-12
Hi,
please can you tell me how did you managed to install DraftSight on 13.10?

I was trying but without any result for now

---

### Post by ping-wu on 2013-10-13
There is DraftSight for 64-bit Windows.  I don't think there is DraftSight for 64-bit Linux yet.

---

### Post by Smask on 2013-10-14
> **gspe said:**
> Hi,
please can you tell me how did you managed to install DraftSight on 13.10?

I was trying but without any result for now

I installed it with Software Center or gdebi/gdebi-gtk, can't remember. What error message do you get?

I've had DS installed for a while and was hampered by the "Failed to load modules. The application will close. Please reinstall the application." modal dialog. No information on stdout. That error went away a couple of days ago. The QGtkStyle stuff you can ignore or run ```
draftsight -style plastique

```
A guy on the DS support forum noticed that he needed to install libcanberra-gtk-module:i386 and libcanberra-gtk0:i386. He installed DS on a clean machine.
```
sudo apt-get install libcanberra-gtk-module:i386 libcanberra-gtk0:i386
```
Me, I might have installed them with Google Earth or Wine or something.

---

### Post by Smask on 2013-10-14
> **ping-wu said:**
> There is DraftSight for 64-bit Windows.  I don't think there is DraftSight for 64-bit Linux yet.

No, but Dassault have got the multiarch memo. (looking at you, Google)

---

### Post by gspe on 2013-10-14
> **Smask said:**
> 
A guy on the DS support forum noticed that he needed to install libcanberra-gtk-module:i386 and libcanberra-gtk0:i386. He installed DS on a clean machine.
```
sudo apt-get install libcanberra-gtk-module:i386 libcanberra-gtk0:i386
```


Thank you......
this two was what i need in order to start DraftSight.

---

### Post by gspe on 2013-10-14
Just for curiosity....
Do you know what kind of graphics libraries DraftSight use?
I ask because it still have horrible graphics performance in Linux 64 and in Windows too!!!
It's almost unusable for serious work... but it's better than nothing.
So I'm curious to know what they use.

---

### Post by Smask on 2013-10-14
> **gspe said:**
> Just for curiosity....
Do you know what kind of graphics libraries DraftSight use?
I ask because it still have horrible graphics performance in Linux 64 and in Windows too!!!
It's almost unusable for serious work... but it's better than nothing.
So I'm curious to know what they use.

Qt4 for menus and dialogs. Dunno about the graphics stuff. 

Bugs so far in V1R4:

Opening multiple files makes DS to only display the contents of the last one selected. You have to flip between model and layout tab to show the contents of the other drawings.

Printing: 

Default settings just sucks. No, I don't want to print on a index card sized paper, I don't need to print on Japanese envelopes either. I don't want to fit my drawing on said index card. And when fitting drawing to paper size it won't print it the scale of that paper. Apparently index card(76x127mm) is larger than A4. Selecting A4 and fit to said A4 will fit the drawing to 210x297mm which make the outermost lines disappear in the hard coded margin of the printer with no way of setting the printable area in the software and no way of calibrate the printer. Line thickness gets rounded down to closest 1/64 of an inch, but printing to PDF and then printing that PDF works. Thanks to that rounding bug, I'll have to use 0.4mm and 0.8mm line thickness, which means when printing stuff where lines gets close to each other the printing algorithm remove lines.

---

### Post by sammiev on 2013-10-14
I was able to install on a 64 bit OS with no issues. Will let my little girl play with it.

---

### Post by Smask on 2013-10-15
> **sammiev said:**
> Will let my little girl play with it.

Girls and design usually means cats an dogs and flowers and such things. Don't let that fool you, as soon as you look away there will be killer robots and slaughterhouses. They can't be trusted.

---

### Post by Ralph_Lam on 2014-01-25
please give me the order in which you did things which allowd you to run draftsight.

When do you enter

sudo apt-get install libcanberra-gtk-module:i386 libcanberra-gtk0:i386

?

---

### Post by Ralph_Lam on 2014-01-28
Linux Mint, which is supposedly based on Ubuntu, has a package handler that, when I click on the ubuntu version of Draftsight on the desault site, and select to open with that package handler by default, installs draftsight flawlessly, and Draftsight runs better on Mint than it does on Windows.

So...when I am in Ubuntu, it uses a different package handler, and that seems to go just as smoothly as the Mint handler, but then at the end, it gives errors and won't go further.

The package handler for SolydK works for installing the Ubuntu version from the desault site.
The package handler for Mint works for installing the Ubuntu version from the desault site.
The package handler for **UBUNTU** does _NOT_ for installing the **UBUNTU** version from the desault site.......

what am I missing?

---

### Post by cariboo on 2014-01-29
Have you got gdebi installed?

---

