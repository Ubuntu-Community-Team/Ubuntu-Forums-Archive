---
title: "Fonts messed up in Wine"
date: 2008-12-08
forum: Wine
---

### Post by matthewm27 on 2008-12-08
I have ubuntu installed, and I installed Wine to install Dreamweaver, Photoshop, etc, I installed everything, and the fonts are not working at all. They are smooshed together and look horrible. I have already tried copying the fonts on my Windows partition to the fonts folder in Wine... and NOTHING. Please help. I have attached a picture that explains what it looks like.

---

### Post by matthewm27 on 2008-12-08
Bump

---

### Post by [censored] on 2008-12-10
re bump.

Same problem for me. Wish I could find a solution.

---

### Post by ajcham on 2008-12-10
Try

[FONT="Fixedsys"]sudo apt-get install msttcorefonts
[/FONT] 
(or install the package using Synaptic if you prefer)

---

### Post by matthewm27 on 2008-12-11
Thanks for the re bump censored. Ajcham, The link you gave me didn't work.

---

### Post by SocratesTNR on 2008-12-11
I had the same problem. The solution was to add a line to some kind of configuration file. Sorry, can't remember anymore details than that.

I've moved my copy of Photoshop, off my old i486 Windows 95 box and on to my new, running wine under ubuntu. Quite peachy.

---

### Post by ajcham on 2008-12-11
> Ajcham, The link you gave me didn't work.

Do you mean it wouldn't install, or installing didn't fix the problem?

If the former, make sure you have the multiverse repository enabled (there'll be some info somewhere in the forums if you are unsure how to do this).

If it's the latter, I'm afraid I can't help any further.  When I had font problems in Wine installing this package fixed it.  Not sure what else the cause could be.

---

### Post by matthewm27 on 2008-12-11
It installed, but didn't fix the problem. I can try to reboot, but I hate doing that because I have to reconfigure my resolution every time I reboot due to a video driver problem.

---

### Post by ajcham on 2008-12-11
Rebooting wouldn't make a difference.

Sorry I couldn't be of any help.  Hope you get the issue (and your graphic driver problem!) sorted.

---

### Post by matthewm27 on 2008-12-11
Its ok :D thanks for the help anyway.  P.S: My graphic driver problem is that my screen pans. I can only view 640x480 of my screen, but my resolution is 1024x768.

---

### Post by beyboo on 2008-12-11
Did you install the MS Corefonts using Winetricks. Download it here[[http://www.kegel.com/wine/winetricks]](http://www.kegel.com/wine/winetricks]). Its a script, save it say in your home folder and run 
> chmod +x winetricks
./winetricks

Select the MS fonts and see if it makes a difference

Edit : Before you start using winetricks, do run a "sudo apt-get install cabextract". Its needed for installing from all  those cab files winetricks downloads.

---

### Post by [censored] on 2008-12-11
Well whatever you do, don't do wineboot. I just tried that, and about half a dozen boxes popped up, with information I couldn't read because the fonts are all screwed up. I tried pressing the buttons, and they wouldn't go away. I tried killing wine at the command line, but the boxes kept re spawing. In the end I had to restart to get rid of them.

---

### Post by mplexus on 2008-12-15
[http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+fonts](http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+fonts)

---

### Post by [censored] on 2008-12-17
Your solution, courtesy of one Bakon Jarser 

[http://ubuntuforums.org/showpost.php?p=6371894&postcount=5](http://ubuntuforums.org/showpost.php?p=6371894&postcount=5)

---

