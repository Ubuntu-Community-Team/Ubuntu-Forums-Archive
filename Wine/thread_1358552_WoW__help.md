---
title: "WoW  help"
date: 2009-12-18
forum: Wine
---

### Post by charlton2142 on 2009-12-18
Hello I'm attempting to install WoW under the wine software. First I installed The regular WoW without any problems and then I proceeded to try and install WoTLK where i run into an error telling me that I don't have enough space. It reads:

"Sorry, the installation failed.

The disk doesn't have enough free space to install Wrath of the Lich King. (More than 10.1 GB is required, but only 0.0MB is available.) Please free up space."

I checked my hard drive and i have 87GB left free please help

thanks

---

### Post by beastrace91 on 2009-12-18
Try the following command in terminal (replace **username** with your login name): ```
sudo chown -R username ~/.wine
```

Then try running the game.

Regards,
~Jeff

---

### Post by charlton2142 on 2009-12-18
I did, same error.

---

### Post by Alatar1 on 2009-12-19
The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".

FYI : once you get it installed,  In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".
DO NOT USE THE LAUNCHER! it WILL lock you out again!!! this should fix this issue.

---

