---
title: "Nothing will uninstall in wine"
date: 2009-03-01
forum: Wine
---

### Post by josephellengar on 2009-03-01
Hi.  I've got a wine bottle that I use for MS office and a bunch of other stuff.  Anyway, I want to uninstall everything except for MS office (safari, audible, apple update manager, some other stuff), but none of it will uninstall.  I don't want to completely reinstall wine because that would entail reinstalling and recustomizing my whole office thing.  What could I be doing wrong here?  Is there anything else I can try?

---

### Post by cogadh on 2009-03-01
How are you uninstalling the apps, using the application's own uninstaller or Wine's uninstaller?

---

### Post by josephellengar on 2009-03-01
> **cogadh said:**
> How are you uninstalling the apps, using the application's own uninstaller or Wine's uninstaller?

both

---

### Post by cogadh on 2009-03-01
What exactly happens when you run the uninstaller (either method)? Does the unistall process appear to run at all? Are the program directories at least removed (menu shortcuts should be left behind)?

---

### Post by Milv8 on 2009-03-02
Hi All

I have the same problem as above when you unistall programs in wine,the program doesnt work but you can still see the programs. 

I tried to take a screen shot to show which have been unistalled and still appear.

Regards
Milv8

---

### Post by cogadh on 2009-03-02
If you are tallking about the menu shortcuts still showing up after uninstalling something from Wine, that's normal. You need to manually delete the shortcuts.

---

### Post by josephellengar on 2009-03-02
> **cogadh said:**
> What exactly happens when you run the uninstaller (either method)? Does the unistall process appear to run at all? Are the program directories at least removed (menu shortcuts should be left behind)?

The uninstall process did run, but it wasn't uninstalled and still showed up in the menu for what I can uninstall.  It still ran when I clicked on it (this is opera, firefox, audible).  For Safari and the other apple things that I had installed, when I told them to uninstall they decided to install instead (the thing that popped up told me they were installing).  Weird.

---

### Post by cogadh on 2009-03-02
Weird, but not all that uncommon (happens all the time with certain installers). After you run the uninstall process, go to the Program Files directory and manually delete the application's installation directory. This doesn't always work, but if you try to run Wine's uninstaller again, it will complain that it can't find the necessary files and will remove the entry from the uninstaller list. If that doesn't work, then you will probably need to also manually remove the registry entries for each installed app, after deleting their program directories.

I really hate to say it, but in the long run, it might just be easier to delete your .wine directory and start fresh with a clean install of Office. Once you have it installed and running, don't install anything else on that wineprefix, instead create a new wineprefix for any other apps you want to install, that way you won't risk screwing up your Office install ever again.

---

### Post by josephellengar on 2009-03-02
> **cogadh said:**
> Weird, but not all that uncommon (happens all the time with certain installers). After you run the uninstall process, go to the Program Files directory and manually delete the application's installation directory. This doesn't always work, but if you try to run Wine's uninstaller again, it will complain that it can't find the necessary files and will remove the entry from the uninstaller list. If that doesn't work, then you will probably need to also manually remove the registry entries for each installed app, after deleting their program directories.

I really hate to say it, but in the long run, it might just be easier to delete your .wine directory and start fresh with a clean install of Office. Once you have it installed and running, don't install anything else on that wineprefix, instead create a new wineprefix for any other apps you want to install, that way you won't risk screwing up your Office install ever again.

I'll do that.  Thank you for your help.

---

### Post by Meow27 on 2009-03-02
and noone asks for the version of wine?

---

### Post by Milv8 on 2009-03-03
Hi There

Wine Ver 1.1.7

regads
Milav8

---

### Post by Meow27 on 2009-03-03
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

try updating

---

### Post by ahammedali on 2009-06-25
hellow i have this same problem, i searched more bt can't find a good methode to solve this problem, bt i've solved by another methode, by istalling a software, named uninstaller on wine, and open that then we can uninstall any software installed on wine. this is the link to download uninstaller  [http://www.revouninstaller.com/revo_uninstaller_free_download.html](http://www.revouninstaller.com/revo_uninstaller_free_download.html)  reply if you have solved ur problem to my email [email]ahammedlai.akbar@gmail.com[/email]

---

### Post by andrea000 on 2009-06-25
I had to delete the wine folder then remove wine from
synaptic then reinstall it and all was fine

---

