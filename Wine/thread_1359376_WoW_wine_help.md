---
title: "WoW wine help"
date: 2009-12-19
forum: Wine
---

### Post by charlton2142 on 2009-12-19
Hey guys I need some help with file permissions. I currently have WoW fully installed and its running alright but everytime I want to start it up i have to change the file permissions by navigating to: .wine/drive_c then I have to run "sudo chmod a+rwx World\ of\ Warcraft"

After the game is exited the permissions on the folder revert to locked. if anyone could help me change this it would be appreciated 

thanks

---

### Post by Alatar1 on 2009-12-19
The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".
Now that that is set, In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".
DO NOT USE THE LAUNCHER! it WILL lock you out again!!! this should fix this issue.

IF while working on the issue above, you cannot change file permissions due to it telling you the owner is "root"...
you will need to change the permissions as root,
the way i know how to do this is go to terminal and enter
Code:

sudo nautilus

or whatever file browser you use (nautilus is the default for ubuntu) this will allow you browse files as root,
BE VERY CAREFUL HOWEVER, Tinkering with files as root can have very bad consequences and compromise your machine possibly, that being said...
simply browse to the directy as stated above and change the permissions that way...there are also console commands to do it manually, but for the sake of the not so savvy, I've omitted those.

---

