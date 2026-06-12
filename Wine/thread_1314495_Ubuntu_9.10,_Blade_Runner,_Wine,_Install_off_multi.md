---
title: "Ubuntu 9.10, Blade Runner, Wine, Install off multiple CDs?"
date: 2009-11-04
forum: Wine
---

### Post by kawazu on 2009-11-04
Folks;

maybe a thoroughly trivial question, but for the sake of entertaining an old enthusiasm of mine, I just tried to install an old Windows9x game ("Blade Runner", to all those who know...) using Wine on Ubuntu 9.10. Haven't tried this in ages. Failed again, this time.

Situation: The game itself spans four CDs. No matter whether I try to install everything (requiring to swap CDs during installation) or try to do a minimum install (requires just the first CD IIRC but asks me to change the medium once in a while), I regularly end up with having to eject the CD and insert a new one which is not possible as the CD obviously is mounted.

Doing a quick look around winehq.com, the usual hint for situations like this is to use "wine eject" ... which however doesn't seem to work in 9.10 (hal keeping the device occupied no matter what I try)?

So ... any known workarounds how to install the given game (and/or potentially any other Windows application using > 1 installation medium) using wine and 9.10?

TIA and all the best,
Kristian

---

### Post by dearingj on 2009-11-04
Perhaps try copying the CDs to your hard drive and installing from there?

---

### Post by tyle on 2009-11-05
> **kawazu said:**
> 
So ... any known workarounds how to install the given game (and/or potentially any other Windows application using > 1 installation medium)
Kristian

My hint would be to try to run the installation without cd:ing to the CD folder, that is
```
wine /path/to/application.exe
```
rather than
```
cd /path/to
wine application.exe
```

The times I have had problems with wine eject, it turned out to be that it refused to eject since the cd directory was the present work directory of my terminal.

Hope this helps.

---

### Post by kawazu on 2009-11-05
Folks;

first off, thanks a bunch for your comments on that, much appreciated. :)

Things I learnt so far:


> **tyle said:**
> My hint would be to try to run the installation without cd:ing to the CD folder, that is
```
wine /path/to/application.exe
```
rather than
```
cd /path/to
wine application.exe
```


This fails. It fails same as copying all the CDs to hard drive and trying to run setup.exe from there fails, ending in an error message telling me that some "important files" have not been found and I please shall re-run setup.exe directly off the CD. :( Thought about eject indeed being troublesome when cd'ing to the CD mount point before running setup... :(

Any other ideas?
Thanks in advance and all the best,
K.

---

### Post by Acid_1 on 2009-11-06
Hi! I'm having the exact same problem with Civilization 4. It requires 2 discs and when I try to insert the second, well, I end up with the same problem. In fact, when I try to force unmount the disc, then stick in disc 2, I have to restart my PC before it even recognizes it as a different disc! Any clues?

---

### Post by petition on 2010-03-02
I'm a big noob who's running karmic with the newest update of wine from winehq. I had the same problem, but got it to work.

I was trying to install baldur's gate 2 -- when i tried to change disks, it would eject the disk but not unmount it, so it wouldn't acknowledge the new one and i'd need to close the installer, then unmount the disk that was no longer in the drive before it would let me eject the second one. here's what worked for me to fix that.

I opened the disk (for me, media/cdrom0), right clicked the setup file (called baldur.exe in this example), and chose open with wine installer. I figure this has the same effect as what the poster above suggested, running the setup without cd:ing to the CD folder. When the install reached the point where i needed to change disks, i opened a terminal and told it 

wine eject d:

it ejected the disk, and then worked fine when i put in the next one.

it sounds like you already tried this kawazu, and im a beginner so this is probably obvious, but i hope this can help someone.

---

