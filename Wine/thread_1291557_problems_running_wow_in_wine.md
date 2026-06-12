---
title: "problems running wow in wine"
date: 2009-10-14
forum: Wine
---

### Post by theoak on 2009-10-14
ok so when i try and open wow.exe file in wine i get an error msg saying the program ran into a serious problem and needs to close. i have no idea what i need to do to fix it. i tried looking yesterday all day to find anything that would help, i came up with nothing. 

just hoping for a little feed back on how to correct this error. ill attach the error msg.

Thank you for helping.

---

### Post by superdav42 on 2009-10-14
Did you check the wine [app db]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421") I would do everything it suggest here. Do you actually get wow installed or does it give this error while installing. As it says you have to use 1.0 or 1.1.26 to install it. To play you have to set it to use opengl ie ```
wine wow.exe -opengl
```

---

### Post by theoak on 2009-10-14
yeah ive looked at it tons of times... i added the opengl thing to the .exe and now i get this error.

and yes i installed from the website it installed into this file. now the wow.exe didnt show up on my desktop or anything but its in the file folder with all the installed things for wow.

/home/theo/.wine/dosdevices/c:/Program Files/Common Files/Blizzard Entertainment/World of Warcraft Installer/World of Warcraft - this is where the program was saved and installed to. is it a problem running it from here?

---

### Post by Drasticly on 2009-10-15
Try to cd into /home/USERNAME/.wine/drive_c/Program Files/World of Warcraft/WTF
Once there, type pico Config.wtf (or whatever the .wtf file is named for you - might also be RunOnce.wtf) Within that file, copy and paste the following:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"

Hope this helps mate.  Please let me know.

---

### Post by BenAshton24 on 2009-10-15
Some terminal output would be nice as well :)

---

