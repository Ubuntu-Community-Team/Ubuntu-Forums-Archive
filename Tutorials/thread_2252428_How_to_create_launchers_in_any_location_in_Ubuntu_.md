---
title: "How to create launchers in any location in Ubuntu Mate"
date: 2014-11-11
forum: Tutorials
---

### Post by stevecook on 2014-11-11
As you may already know, if you are on the desktop in Ubuntu Mate, you can right click and one of the menu options is to create a launcher. This option, however, is not available when you are anywhere in a folder in your home directory or in a folder you may have created on the desktop. In other words, the option is only available on the desktop itself. The following tutorial shows how you can add a right click menu item that will allow you to create a launcher anywhere in your home location as well as on the Desktop or inside a folder on the desktop.
 
 I should say, the following involves installing gnome panel which, possibly, may have other unwanted effects on your Ubuntu Mate system. However, I have certainly not experienced any difficulties since installing it on my Ubuntu Mate system. But, I thought I should make mention of it so you are aware. Anyway, here's how you do it:
 
 1) Open a terminal and type:
 
**  sudo apt-get install gnome-panel**
 
 Close the terminal once installation has completed.
 
 2) Open up a text editor and paste the following into it:
 
**  gnome-desktop-item-edit ./ --create-new**
 
 Save the file as "create-launcher-in-this-location.sh" (or any other name you wish. Just make sure to end it with ".sh")
 
 3) Open a terminal and go to the directory where you have saved the file.
 
 Type:
 
**  sudo chmod +x create-launcher-in-this-location.sh**
 
 This makes the file executable
 
 Close the terminal
 
 4) Navigate via the file manager to where you saved your file and right click it and choose "copy". After you have done this navigate to your home folder (if you are not already in it) and press CTRL-H. This will display all of the hidden folders. Navigate to "/home/user/.config/caja/scripts" (where "user" is your username). Once inside this folder, right click and choose "paste". The "create-launcher-in-this-location.sh" file will now appear in this location. Close the file manager.
 
 5) From now on, wherever you are in your home folder or on the desktop, if you right click you will see a new option called "scripts". Inside that option is your "create-launcher-in-this-location.sh" file. If you choose it, a standard launcher dialogue box will apear and you can proceed to create the launcher. The launcher will subsequently appear inside your currently active location/folder. You can even use this script on your desktop instead of the standard option in the right click menu that already exists if you want to.
 
 One final thing you may need to do following implementing all of the above is to go to your menu and navigate to system/preferences/preferred applications, choose the "system" tab and re-assign "caja" as your preferred file manager, I found, after installing Gnome Panel, that it had defaulted to "files" file manager. Which, presumably, comes with Gnome Panel. Other than that, it doesn't seem to have affected anything.

---

### Post by tgalati4 on 2014-11-12
Rather than possibly breaking your system with two panels, can't you just create launchers on the Desktop, then go to the Desktop in *caja* (Nautilus clone in MATE) and move them to the directory where you want them?

There is probably a way to put "Create Launcher" in *caja*, but it would require some searching.  I've customized Nautilus menus before, so it must be similar.

---

### Post by mc4man on 2014-11-12
The use of sudo to make the file exectuable seems unnecessary, as does creating the file twice. Why not just create it in /home/user/.config/caja/scripts in the 1st. place & mark executable (no sudo

---

### Post by stevecook on 2014-11-24
update:

I now realise you don't even need to install gnome panel. Simply change:

**  gnome-desktop-item-edit ./ --create-new**

to

**  mate-desktop-item-edit ./ --create-new**

.....and it will work. All other instructions remain the same.

---

