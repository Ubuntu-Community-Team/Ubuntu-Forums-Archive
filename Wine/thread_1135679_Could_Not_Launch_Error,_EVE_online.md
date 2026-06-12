---
title: "Could Not Launch Error, EVE online"
date: 2009-04-24
forum: Wine
---

### Post by thesushiking on 2009-04-24
When i try to run eve through wine, i.e. wine --> programs --> eve i get this error:

Failed to change to directory '/home/jackson/.wine/dosdevices/c:/windows/temp/nsn5f75.tmp' (No such file or directory)

HOwever, 

if i open wine and explore drive C and find the eve EXE file and right click on it and open it with wine, eve runs fine. But thats the long way. Any reason why wine is doing this when trying to run it normally?

I'm using Unbuntu Jaunty.

---

### Post by =^,^= on 2009-04-25
Try changing the path to eve.exe in the shortcut!

---

### Post by softdel on 2009-04-25
This is a valid bug.. happens to a lot of wine stuff.

---

### Post by actinium on 2009-05-24
this also had been bugging me for a while too.. and here is the solution:

change the shortcut manually.. not via the menu options. The menu shortcut should be located in ~/.local/share/applications/wine/Programs/, remove the line where the hidden option Path, where it is pointing to the non-existent .tmp file and it should run fine. 

cheers,

Alan

---

