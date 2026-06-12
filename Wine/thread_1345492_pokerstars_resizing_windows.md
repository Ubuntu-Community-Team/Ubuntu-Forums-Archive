---
title: "pokerstars resizing windows"
date: 2009-12-04
forum: Wine
---

### Post by da133 on 2009-12-04
I was reading about how to get pokerstars to be able to resize windows under wine, and this was the instructions:

**Manually resizing table windows workaround:**   
[LIST]
[*]You can resize and then redraw the table using the F5 key by adding the following into the *~/.wine/drive_c/Program Files/PokerStars/user.ini* file under [Options]: **f5redrawtable=1** (won't work properly if window is resized beyond min/max size)
[/LIST]
I'm new to ubuntu, is this something you type into the terminal? Because when I typed that into the terminal I got this message:

greg@greg-desktop:~$ "~/.wine/drive_c/Program Files/Pokerstars/user.ini"
bash: ~/wine/drive_c/Program Files/Pokerstars/user.ini: No such file or directory

I also tried searching for user.ini with no luck

---

### Post by sylentdogg on 2009-12-04
What this means is you need to modify the user.ini file in a text editor(gedit). The .wine directory is a hidden directory because of the period in front of the name. So if you open up your user folder(greg) and under view, check show hidden files, it will show you the .wine folder. In that folder you will find drive_c/Program Files/Pokerstars and then you should find the user.ini file. You will have to open that file and modify as per the directions. Also, when you see a ~/ it means your home folder so ~/.wine/drive_c/Program Files/Pokerstars would be in your home folder. I hope that clarifies thing a little for you.

---

