---
title: "Wine games shortcuts, main menu"
date: 2009-10-16
forum: Wine
---

### Post by Joezorry on 2009-10-16
Hello!
I'm running jolicloud, which is basically Ubuntu with UNR.

I have some games that I've put in the games main menu.
It works fine when I click on the .exe file in the folder, but when I place a shortcut in the main menu it won't work.
Some games work but some don't.

Those who don't are: Commandos behind Enemy Lines, Starcraft, Crimsonland etc.

Like I said works great when I click on .exe in the folder, but when I put it in the Main Menu - Games, it don't work.

Any solutions?

---

### Post by beastrace91 on 2009-10-16
You need to tell it to run the .exe file using Wine (which is what you are doing when you double click the .exe file) Simply pointing a menu entry to the windows executable means the system trys to run it like a native file.

To do this simple add wine before the path to .exe file for the game you are trying to run. For example: ```
wine ~/Downloads/MyGame/mygame.exe
```

Let me know if you need further help accomplishing this,
~Jeff

---

### Post by Joezorry on 2009-10-16
Thanks for you reply :)
Nope the problem still is there.
tried writing wine ~folder1/folder2/game.exe
it should start then right?

The strange thing is that Diablo 2 and Peggle can both run from the main menu, but not Commandos or Crimsonland etc.

Feel like my knowledge don't go too far ahead. Not sure if I should use '/' or '\' when open things in wine.

Can you elaborate on what you said or do you have another solution?
It would be greatly appreciated.

---

