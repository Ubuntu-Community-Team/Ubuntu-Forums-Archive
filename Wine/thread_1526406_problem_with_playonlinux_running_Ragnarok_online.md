---
title: "problem with playonlinux: running Ragnarok online"
date: 2010-07-08
forum: Wine
---

### Post by luca_blight05 on 2010-07-08
Ok.. at first i had problems on how to install the game because after i select RagnarokOnline in the PlayonLinux choices and hit APPLY, it just freezes.. So i Force Quit it.. then suddenly a window pops out and says that it will install Ragnarok and then when i hit forward it is asking for my installer... so there i installed RO on linux... another problem came up, playonlinux cant find the directory where i installed my RO, so there ive solved it and copy paste the directory and renamed the folder into where it is targeting. ***NOW THIS IS MY PROBLEM..***

```

Checking python :                 [ Ok ]
Running Ragnarok Online
Ragnarok Online: line 4: cd: /home/USER/.PlayOnLinux/wineprefix/RagnarokOnline/drive_c/Program Files/Gravity/RagnarokOnline: No such file or directory
wine: cannot find L"C:\\windows\\system32\\Ragnarok.exe"
Running Ragnarok Online
Ragnarok Online: line 4: cd: /home/USER/.PlayOnLinux/wineprefix/RagnarokOnline/drive_c/Program Files/Gravity/RagnarokOnline: No such file or directory
wine: cannot find L"C:\\windows\\system32\\Ragnarok.exe"

USER@ubuntu:~$ playonlinux
PlayOnLinux v3.7.3

Checking python :                 [ Ok ]
Running Ragnarok Online
Ragnarok Online: line 4: cd: /home/USER/.PlayOnLinux/wineprefix/RagnarokOnline/drive_c/Program Files/Gravity/RagnarokOnline: No such file or directory
wine: cannot find L"C:\\windows\\system32\\Ragnarok.exe"
Running Ragnarok Online
Ragnarok Online: line 4: cd: /home/USER/.PlayOnLinux/wineprefix/RagnarokOnline/drive_c/Program Files/Gravity/RagnarokOnline: No such file or directory
Running Ragnarok Online
Running Ragnarok Online



```as you can see... my previous problems were solved but then when i hit the RUN button, the terminal says "Running Ragnarok Online" but nothing happens.. i dont get it... i placed everything it's asking. what should i do?

---

### Post by luca_blight05 on 2010-07-10
aww.. howcome there are 53 views but not even a single reply... hey guys? help... :(

---

### Post by cogadh on 2010-07-11
Probably because your problem explanation isn't terribly clear at all. I've read it three times now and I'm still not sure exactly what you did. 

It appears that when you try to run the game, it isn't even looking in the game's install directory for the executable, which usually indicates a problem with how or where you installed it or with how it is being run. I would recommend you start over, wipe out then re-install POL and Wine, install RO, then try running it. If it doesn't work, don't try to fix it, post back here with precisely what happened, including the exact details of any error messages or terminal output. If we go through what is happening step-by-step, it should make things much clearer.

---

