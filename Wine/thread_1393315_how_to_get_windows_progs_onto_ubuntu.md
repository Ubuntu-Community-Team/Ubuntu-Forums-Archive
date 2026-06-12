---
title: "how to get windows progs onto ubuntu"
date: 2010-01-29
forum: Wine
---

### Post by angliski on 2010-01-29
Sorry to thick, but during my ubuntu 9.1 install I didn't create a virtual c\ drive.

In the config wine screen it shows me the drive, but when I go to programs to add programs to the config it is blank.

Is there a way of moving my windows vista files onto ubuntu. can I just move the program files that I need or do I need the whole windows installation and will it take the same amount of space on my ubuntu partition?

Thanks 

Steve

---

### Post by 23dornot23d on 2010-01-29
I just open my Vista Drive in a window ..... using Nautilus ot Thunar or Dolphin

Go to the Programs Directory on the C: Drive ........ and run the programs ,,,,,

you need WINE installed though ...... install it with 

sudo apt-get install wine

in a terminal Window ....... not all files will run ...... but a lot do ........ check it out ......

This way you do not need to re-install ..... ( its one of the ways I do it ,,,,, and it works for me  .... )

You can install direct into UBUNTU ..... but as you will see it creates a different directory

___________________________

Question ...... How did you install UBUNTU onto your System ....... ? .............. 
 ( its just that there are a few ways of doing it now ......... but as long as you can get to the proper C: drive it should work  )

---

### Post by ajgreeny on 2010-01-29
In my experience, which is now pretty old for wine (I don't need anything from Windows any more), there are only a very few programs that will run direct like that from your windows install partition, though it is worth trying.  Normally you install wine, then using wine you install the windows application from its own installer files or CD using the command in terminal ```
wine /path/to/install/exe/file
```or by right clicking on the exe install file and choosing "Open with wine"

Don't expect too many programs to run though.  Some will do with everything working, some with only limited bits working, but many more will just give you error messages and not run at all.

---

