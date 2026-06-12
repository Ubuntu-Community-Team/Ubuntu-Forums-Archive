---
title: "[SOLVED] In WoW but have a problem"
date: 2009-01-10
forum: Wine
---

### Post by demonicx9 on 2009-01-10
So far everything was running Damn good in WoW for a few mins and i went to dalaran and then once i got inside i wlaked around a lil and All of a sudden Text Started Flying everywere u could say. all the text is removed from where its supposed to be and gos to the text box and Jubmles around i guess.

now just so you all know i just got WoW Working Yesterday. im also useing Interpid another thing is im New to Linux but iv been learning lots :P

would be nice if anybody knows whats wrong cause its kinda Frusterateing

---

### Post by demonicx9 on 2009-01-10
ok guys i havent gotten anything so maybe a screen shot will work so i got one.
sorry about the Double post btw :)

---

### Post by pissedoffdude on 2009-01-10
What kind of graphics card do you have?  Try some of the fixes listed here  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154")

---

### Post by Elviswind on 2009-01-10
If I remember correctly, the white mini-map is due to ATI drivers . . .  have you tried updating if you, in fact, are using an ATI GPU?

---

### Post by demonicx9 on 2009-01-10
I am useing an ATI driver i dont know where to update it unless it dose it Automaticly.
not only thta but if u notice can you all tell about the text? its really screwwwwweed :( can anybody help me plx?

---

### Post by demonicx9 on 2009-01-11
ok well iv tryed some things and still no fix...anybody got anyideas? it would be greatly appriciated. Just so you guys know im useing a ATI radion 300x Graphics card. yes the driver is updated.

and i mean it runs fine at some palces and it dose all that Crap i duno whats wrong but its really anoying..

---

### Post by demonicx9 on 2009-01-11
aha...seems it was the Minimap doing the screwy Text stuff :O! and i found an easy way to go around the Minimap too just Download.

[http://wow.curse.com/downloads/wow-addons/details/hidemini.aspx](http://wow.curse.com/downloads/wow-addons/details/hidemini.aspx)

this addon and it removes ur Minimap and it takes up basicly no space at all and is easy as hell to use i think theres even a way that u could toggle it on and off so if ur outside or anything :P. anyways thats how i got mine working :D

---

### Post by Eviljim on 2009-01-11
The minimap issue is a long standing bug for ATI users, and relates to the driver not being programmed to handle pbuffers (which the minimap uses).

Nvidia cards are not affected by this, and usually on an ATi card the map goes white while inside. Sometimes it can also cause screen tearing as you experienced.

---

### Post by gettensome on 2009-01-11
If I remember correctly adding this to your registry in wine will take care of this; 

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

BTW that String value was added to OpenGL and you have to creat the openGL folder as well.

I use these guide to install and set-up WoW on linux;

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/]("http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/")
[http://www.wowwiki.com/Wine_(software)]("http://www.wowwiki.com/Wine_(software)")

---

