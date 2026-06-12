---
title: "Running esword - problem"
date: 2008-03-27
forum: Ubuntu Christian Edition
---

### Post by JFonseka88 on 2008-03-27
I can't run esword, I installed it and updated modules then I updated WINE, but when I click on it, it just doesn't open.

I'm fairly new to linux, where the hell is my disk drive to be found

---

### Post by david_kt on 2008-03-27
Please try below instruction carefully from the start:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

You should have fully working e-sword.

DK

---

### Post by JFonseka88 on 2008-03-27
How do I find this directory:

 ~/.wine_Esword/drive_c/windows/system32

---

### Post by david_kt on 2008-03-28
> **JFonseka88 said:**
> How do I find this directory:

 ~/.wine_Esword/drive_c/windows/system32

First of all, you need to create that folder with below command:

[wineprefixcreate --prefix .wine_Esword]("wineprefixcreate --prefix .wine_Esword")

After that you will need to "show hidden files" in nautilus:

Open home folder (Places >> Home folder)
Show hidden folder (View >> Show Hidden Folder)

and you will see folders with dot in front.

DK

---

### Post by Eutaw on 2008-03-29
DK,
THANKS! After following the instructions, I got esword up and running with all my fav addons. Had to rename k&d.exe (Keil and Delitzch OT commentary) because bash didn't like the ampersand. Used GUI right click on desktop icon to rename.
Do I have to leave those .exe files on the desktop now that they've been activated in esword? If not, do I just drag them to trash, or what?
Thanks again, great job!
Rick

---

### Post by david_kt on 2008-03-29
> **Eutaw said:**
> 
Do I have to leave those .exe files on the desktop now that they've been activated in esword? If not, do I just drag them to trash, or what?
Thanks again, great job!
Rick

The exe files are not required anymore, unless you want to reinstall. You could just press delete to delete it.

DK

---

