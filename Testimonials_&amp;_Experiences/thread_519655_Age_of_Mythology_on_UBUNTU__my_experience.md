---
title: "Age of Mythology on UBUNTU :: my experience"
date: 2007-08-07
forum: Testimonials &amp; Experiences
---

### Post by xavier_r on 2007-08-07
It ran... it was great...
except for the fonts which were not coming in the menu... anyways, the game font was clear...

Check out the screenshot... :lolflag:
Now one more reason, why I dont need to have windows... :)

---

### Post by Pathfinder_ on 2007-08-08
Did you get muliplayer(ESO) to work?

---

### Post by xavier_r on 2007-08-09
> **Pathfinder_ said:**
> Did you get muliplayer(ESO) to work?

Hey dude :)
As already said, the fonts in the menu were not showing...
So frankly I dont know where to click to start with multiplayer...

Attached is a screenshot of the menu... if u want to know what i mean :)

---

### Post by kostkon on 2007-08-09
I am pretty sure you are missing a font that's why you cannot see the text of the menu options. AoM asks for a font that *Wine* is not able to provide.

Of course, the problem is to find which font it's the one missing. The first thing you could do is to check if you have the Microsoft core fonts installed. If you haven't then search Synaptic for the package *msttcorefonts* and install it.

Another way is to just open a terminal and install them from the command line like this:
 
```
sudo apt-get install msttcorefonts
```

Then, run the game and check if now your problem is solved.

Another thing you could do is to check the main folder of the game, and its sub-folders, for font files. I mean files with the .ttf extension.

If you don't find any fonts there, try to search the CD of the game, maybe there would be some there.

If you find some, then try to copy them to the Windows **fonts** folder that you can access easily. 

Just open a *Nautilus* window, then go to the **View** menu and select **Show Hidden Files**. Afterwards, find the **.wine** folder, then go to the **.drive_c** and then **Windows** folders. Inside you will find the **fonts** folder and there you should copy the font files you found.

Again, run the game and check if now your problem is solved.

If none of the above works, maybe the game asks for the *Tahoma* font, which is not provided with the Microsoft core fonts package.

Follow the[ how-to here]("http://ubuntuforums.org/showthread.php?t=82318") to help you download and if you want install the *Tahoma* font into your system. Again, take the *Tahoma* font file and copy it to the Windows **fonts** folder.

As a last measure, try to run the game with *Wine* from the command line to see if it will split out any error messages about missing fonts. You could also use it with the debug mode turned on. If you want any help about running *Wine* from the terminal, just ask. :)

I hope I helped you somehow.

---

### Post by kostkon on 2007-08-09
After a little research I did, I found [this]("http://support.microsoft.com/kb/810381").

If read it then you will know what fonts you will have to copy to the Windows fonts folder. Indeed, there is a fonts folder in the CD of the game.

---

### Post by xavier_r on 2007-08-09
Hey thanks dude
I'll try those out and see :)

---

### Post by Pathfinder_ on 2007-08-09
I have microsoft fonts installed and text shows up for me in AoM. However i didn't have to move any of the files at all. just instal fonts and it was all okay.

---

