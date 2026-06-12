---
title: "Age of Mythology - Installation Problem"
date: 2011-05-19
forum: Wine
---

### Post by RevGross13 on 2011-05-19
Hello. I am running Ubuntu 10.04. That in mind, I am trying to install Age of Mythology and the Titans expansion using Wine. However, I keep running into a problem.

After I enter the CD Key, It comes up with an error message saying that the setup cannot open PidGen.dll. However, when I open the folder, I see something titled PidGenx.dll.

What can I do?

---

### Post by bobwyajnr on 2011-05-21
Can you describe how you installed Age of Mythology and how you are trying to install the expansion pack? Did you use POL (Play on Linux) or any other tools?

I will try and take a stab at the problem! It sounds like you installing from a CD or something - right? Paths can get messed up if you just double click on a Windows executable file in a GVFS (**G**nome **V**irtual **F**ile **S**ystem) mounted CD. Wine has the concept of a working directory. The main installer executable will look relative to the current working directory for *.dll*'s and associated *.exe* files. In this case you will get a missing file message or the application installer will just crash out (if it's badly written).

[Check out section 3.2 in the Wine FAQ]("http://wiki.winehq.org/FAQ#head-7b61ed553a40ef7dffbbbf09d9b37027082b1c41") You can go the Gnome terminal route as described there. [I would also advise checking out the Wine user manual (it's available in a friendly PDF format download).]("http://www.winehq.org/documentation") The concepts may not make sense on a first reading!

I think you can use:
```
wine explorer.exe
```
(if it is not in your main [COLOR="Red"]Gnome[/COLOR] menu - [COLOR="Red"]Wine submenu[/COLOR] shortcuts)
to launch a Windows explorer and install from your CD drive. I pretty certain that method will get paths right - sorry I'm nearly 100% command for Wine-related stuff! :popcorn:

If your CD-ROM (as **D:** typically) doesn't show up (normally automatic - but not if a Wine server process is already running) you can run:
```
winecfg
```
(again if it is not in your main [COLOR="Red"]Gnome [/COLOR]menu - [COLOR="Red"]Wine[/COLOR] submenu shortcuts)
go to the drive tabs and 'force' a sensible mount point for drive **D:** (say) - typically point it at the native Linux folder **/media/*<CD_LABEL>*** .

Also if you are trying to run the expansion pack installer from a mounted NTFS partition that can cause 'issues' (I've found anyway - since NTFS is a non-native filesystem - it is accessed using the ntfs-3g driver in user space). 

Hope that helps a bit! ):P
Bob

---

