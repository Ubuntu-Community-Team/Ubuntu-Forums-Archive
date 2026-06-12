---
title: "rise of nations"
date: 2009-03-02
forum: Wine
---

### Post by taboey on 2009-03-02
I am trying to install an old game (rise of nations) and I love this game, I was searching on other forums for the product key-did find it- and after i entered the key in and it let me continue, but the pidgen.dll would not load. the age of mythology one sort of set me off in the right direction. But I think that the pidgen.dll is causing many other probs too, such as my computer is slower, I have a dell precision 340 that is pretty well working.

     sorry for the long message, but please help me so I can play my game again.

---

### Post by FrozenFox on 2009-03-02
What version of wine and ubuntu are you running? If you don't know, open a terminal (under accessories I think?) and do: wine --version to find out wine, and use lsb_release -a to find out which version of ubuntu. In any case, you would be better off asking this in the windows game (Wine) section at [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313) , assuming problems with a dll mean you're trying to run a game with wine. There's a big sticky post in capital letters with multiple asterisks around it in this section of the forum saying not to post windows game questions here, because the wine section of the forum is specialized for that purpose; they dont want the gaming section filled with wine problems or the wine section filled with native linux game problems. I'm not familiar with RoN but this page finds RoN rated silver compatibility in a very old version of Wine, so I would have expected it to be working properly or very close to it by now if this is for the correct game you're trying to install: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4403&iTestingId=10276](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4403&iTestingId=10276)

You might want to run the game from the console and provide us the exact output (wine DragNDropExeToTerminal). The original author of that wine report posted a big long error from such including the line "err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\mnt\\cdrom\\PidGen.dll") not found" . I assume you are having that same problem. If such is the case, you will need to deal with exactly what the error says: you're missing MFC42.DLL. If your error from the terminal is the same, Google for that DLL file or grab it from windows, and put a copy of it (case-sensitive by the way!) in the directory /home/YOUR_USERNAME/.wine/drive_c/windows/system32 or perhaps the game's Program Files folder accordingly (more likely the former).

Probably good to go after that..

---

### Post by wingnux on 2009-03-02
Please, post wine-related questions on the proper forum.

[http://ubuntuforums.org/showthread.php?t=624170](http://ubuntuforums.org/showthread.php?t=624170)

---

### Post by hikaricore on 2009-03-02
It's all good, no one who posts here knows how to read... especially the stickies at the top.

---

