---
title: "How to install Icewind Dale II on ubuntu maverick 10.10"
date: 2010-10-15
forum: Wine
---

### Post by Claus7 on 2010-10-15
Hello,

in order to install the game from the official cd's then the following procedure should be followed:

insert CD 1 on cdrom tray and wait to be mounted. Then you will see an icon on your Desktop which will be the mounted folder with the contents of the game. Navigate to that folder **via nautilus** (and **not** via command line) and go to the setup.exe file.

Right click on that file and choose the option: Open -> Open with -> Other application -> Use a **custom command**. For the command just type wine. That way you will solve many issues in the future *as the one which terminates the installation because of the need to insert the second cd*.

Follow the installation process and when the second cd is needed, open a terminal and type:
**wine eject -a**

The tray will be ejected and you will be able to insert the next cd. Wait some moments so as to be recognized and mounted and then press ok to the dialog of switching disks. The installation should proceed till the disk one is needed one more time.

Open a terminal once again, type the wine eject -a command, eject cd 2, insert cd 1, wait to be mounted properly, press ok and you are finished.

Options like wine setup.exe from terminal **do not** work at the time, so this is the best process to install that game.

Regards and happy retro gaming!

---

