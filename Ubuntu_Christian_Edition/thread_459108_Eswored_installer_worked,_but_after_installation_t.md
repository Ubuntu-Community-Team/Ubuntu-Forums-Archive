---
title: "Eswored installer worked, but after installation the app isn't launching"
date: 2007-05-30
forum: Ubuntu Christian Edition
---

### Post by Isoss on 2007-05-30
Hello

I have installed Ubuntu CE recently and was really pleased and excited when I found the esword installer there! and I went on and installed esword. but unfortunately it didn't work after installation! What could the problem be? I have wine installed! is it about wine?

Please help.

Thanks.

---

### Post by mhancoc7 on 2007-05-30
> **Isoss said:**
> Hello

I have installed Ubuntu CE recently and was really pleased and excited when I found the esword installer there! and I went on and installed esword. but unfortunately it didn't work after installation! What could the problem be? I have wine installed! is it about wine?

Please help.

Thanks. 

Did you use the convert_me script or did you do a fresh install of Ubuntu CE?

Also did you run the eSword Installer? Did it give any errors? If you did run the eSword Installer, with no errors, did eSword start? What happens when you try to launch eSword from the main menu?

Jereme

---

### Post by Isoss on 2007-05-30
Actually I installed used the convert me script. About esword, when I ran the installer everything went fine and seemed to be correctly installed. But whenI tried to run Esword after installation, I found the Esword launching icon instead of the installer and clicked it and nothing happened! no errors! no attempts no nothing!

---

### Post by mhancoc7 on 2007-05-30
Ok, try the following in a terminal window.

```
WINEPREFIX="/usr/local/apps/esword4linux/.esword" wine "/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe"
```

Report any errors that you see.

Jereme

---

### Post by father_je on 2008-01-15
hello, I think I have the same problem with esword, the installation run smoothly but when I try to launch the application nothing happens. 
This is what I get in the terminal window     wine: cannot find '/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe' , what is the problem, pls. help..thank you

---

