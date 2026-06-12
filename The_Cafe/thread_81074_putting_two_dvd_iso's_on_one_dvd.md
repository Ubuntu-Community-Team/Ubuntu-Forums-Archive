---
title: "putting two dvd iso's on one dvd?"
date: 2005-10-23
forum: The Cafe
---

### Post by DarkManX4lf on 2005-10-23
i have two retail games that i bought and i made iso's out of them to make backups, and i was thinking since these two iso's added up in size is less than one dvd, can i put these two iso's on one dvd and have a menu for installation in windows?

---

### Post by audax321 on 2005-10-23
You should be able to. BUT, this will only work if both DVDs are data only. If they have audio tracks, you can't do this. You would have to extract both isos into two separate folders on the final DVD. And then to get the autorun to work you need to create an autorun.inf file that points to the menu you want to lauch. Now, the menu needs to be a win32 application and I would recommend using VisualBasic.NET to write it.

You would need the menu to:
 1: Get the path of its own executable.
 2: Get the drive letter by manipulating the string returned from step 1
 3: Create the string path to each games installer:
           drive_letter from step 1 + :\ + folder_the_game_is_in + \ + setup.exe
 4: Set two buttons on the menu to launch the appropriate .exe

It's a lot of work for just a menu but that is how I would do it (but I've never had a need to do this before so there might be an easier way).

---

### Post by DarkManX4lf on 2005-10-23
thanks, i'll try this out.

---

