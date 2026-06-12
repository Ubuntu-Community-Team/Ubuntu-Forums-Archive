---
title: "can't find app that Wine installed from CD"
date: 2010-06-25
forum: Wine
---

### Post by kihi.lind on 2010-06-25
I have a CD of a kids game that I want to install on a Dell laptop that is reimaged in Ubuntu 9.10.  I installed Wine 1.0.1 from the Ubuntu Software Center.  I then found the Install.exe on the CD, right-clicked and installed with Wine.  Everything went well - the app ran through the standard Windows installation and the app seemed to be installed.  Now I can't find the app to run it with  Wine.  It's a Curious George kids game that I installed in a folder called "CuriousGeorge".  I went looking for a folder with that name, but didn't find it.  How do I find the app that Wine intalled? Please keep in mind that I'm a Ubuntu rookie.

---

### Post by dtfinch on 2010-06-25
Your C: drive in wine is in a hidden directory. If you press ctrl-H in the file browser in your home folder, it'll show hidden files. Then you open the .wine folder, and the drive_c folder within that.

You could also check if there's a working shortcut in you Applications menu, if there's a wine folder on the list. I can't remember if the wine menu is there by default or if I had to enable it by right clicking the Applications menu and choosing Edit Menus, and checking the box next to it.

---

### Post by kihi.lind on 2010-06-26
I have Wine installed on teh Applications menu, and have the Programs menu options in it, but the app I want isn't there.  I went to the home directory and hit CTRL-H and there was no ".WINE" folder.  Any other ideas?

---

### Post by hikaricore on 2010-06-26
If an application didn't make a menu entry you'll have to create on your own.
As far as your .wine folder, yes there is.
You need to show hidden files (ctrl+h) or select it from the view menu.

---

### Post by Loctrice on 2010-06-28
If you don't have a .wine folder, you can just go into the menu and select "configure wine". You don't need to change anything, but opening that the first time creates the .wine

---

### Post by hikaricore on 2010-06-28
If he installed something through wine, he has a .wine folder.
I'm disregarding the possibility that he used a prefix because he can't even find his .wine folder.

---

