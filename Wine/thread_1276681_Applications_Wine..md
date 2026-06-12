---
title: "Applications Wine."
date: 2009-09-27
forum: Wine
---

### Post by LeetNeo on 2009-09-27
Hello, I'm new to the forums.

Anyways, I uninstalled Wine and saw the Wine Applications folder still there. So I go into the main menu and deleted the Wine folder from there. I then installed Wine again, and the Applications Wine folder is not there anymore.

Can anyone tell me how to fix this problem? And give me instructions on how to fix it, since I'm new to using Ubuntu.

The version I reinstalled was version 1.1.28.

Please and thank you.

-LeetNeo.

---

### Post by jasonditz on 2009-09-27
> **LeetNeo said:**
> Hello, I'm new to the forums.

Anyways, I uninstalled Wine and saw the Wine Applications folder still there. So I go into the main menu and deleted the Wine folder from there. I then installed Wine again, and the Applications Wine folder is not there anymore.

Can anyone tell me how to fix this problem? And give me instructions on how to fix it, since I'm new to using Ubuntu.

The version I reinstalled was version 1.1.28.

Please and thank you.

-LeetNeo.

Yes, I had this exact same problem. The fix is really simple, but not obvious:

Edit the following file with the editor of your choice:

~/.config/menus/applications.menu

When you delete the wine section in Main Menu it doesn't actually remove <Name>wine-wine</Name> like you'd figure it would... it's still sitting there. Instead it just puts a <Delete/> key after it. 

Just delete the <Delete/>, save, and your wine menu will be back.

---

### Post by beastrace91 on 2009-09-27
Haha! Super useful to know, I've been having this exact same issue but have been too lazy thus far to do anything about it xD

Thanks much,
~Jeff

---

### Post by LeetNeo on 2009-09-27
I'm confused at what I'm supposed to do since I'm new at using Ubuntu.

Also what editor do you suggest I use, jasonditz?

-LeetNeo.

---

### Post by andrea000 on 2009-09-27
Do a gksu nautilus or sudo nautilus from the terminal
then go to the config/menus/applications.menu and open
it(should just be a text file) find were it has deleted
posted under the name of the menu you want back and remove
the deleted word then your menu will come back.

---

### Post by LeetNeo on 2009-09-27
Hey andrea000, when I type in any of those commands in the terminal, it just brings me to my root folder and does nothing else. It only has one thing in it which is desktop.

-LeetNeo.

---

### Post by andrea000 on 2009-09-27
left hand side click file system sorry i forgot
to tell you that.

---

### Post by LeetNeo on 2009-09-27
For some reason I don't see a config folder in the File System. I also checked "Show hidden or backup files" in the Preferences.

-LeetNeo.

---

### Post by andrea000 on 2009-09-27
from file system go to home then your username
and config/menus/applications.menu

---

### Post by LeetNeo on 2009-09-27
Ok thank you, it's fixed now.

-LeetNeo.

---

### Post by jasonditz on 2009-09-27
Open the file browser (click Places then pick Home Folder or Documents or something)

Control + L to open up the location bar

paste the following:

~/.config/menus

open applications.menu with the text editor of your choice (double click and it will use gedit, which works fine).

---

### Post by LeetNeo on 2009-09-27
Thank you for the reply jasonditz, but andrea000 already helped me. But thanks for you helping me as well.

-LeetNeo.

---

### Post by andrea000 on 2009-09-27
> **LeetNeo said:**
> Ok thank you it's fixed now.

But there's this other problem, when I uninstalled a program, it still shows in the Wine Programs, how do I get rid of that folder?

-LeetNeo.

it's not a folder your talking about the launcher after you
uninstall a piece of software.Go to system->preferences->main menu
click wine on the left hand side then on the right side remove
the checks from the boxes you can also hit delete after you remove 
the check marks but you don't have to do that

---

