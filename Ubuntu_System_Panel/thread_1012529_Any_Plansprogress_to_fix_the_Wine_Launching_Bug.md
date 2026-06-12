---
title: "Any Plans/progress to fix the Wine Launching Bug?"
date: 2008-12-15
forum: Ubuntu System Panel
---

### Post by Ms_Angel_D on 2008-12-15
I was just curious as to the progress of fixing the bug with wine programs not launching. IMHO this is the one issue I can find with USP.

Thanks for any info,
Angel

---

### Post by Malac on 2008-12-16
Hi, which one? :)
This is definitely on my list and high up but I don't run many Windows programs via wine, which creates issues with tracking down where the problems lie.
 The few games/apps I do run via wine all run okay with USP, however these are mostly older games as I tend to use consoles now for gaming.

At the moment I wait until someone posts a problem launching a particular program and tackle it on an individual basis, getting a copy and installing it as needed.(This can be a problem). Most of the time with people it is a wine configuration issue not USP's fault or a command line option that needs enclosing in "" or "escaping out" in someway.

I'm always willing to get info via pm or here to let me know of* any* program/shortcut that doesn't launch properly from USP but does from GNOME. A copy of the .desktop file is cool especially if it is one you created yourself and whether it launches from 
Applications but not Favourites or from Recent but not Applications, etc.

Hope this helps.

---

### Post by Ms_Angel_D on 2008-12-16
Well I currently run Guild Wars, Dreamweaver, Flash8, Fireworks 8, & The Macromedia Extension Manger Via Wine, those are pretty Much it. But none of them will launch via USP I can get them to work by using [this fix]("http://ubuntuforums.org/showpost.php?p=2175127&postcount=91") but it's a pain to have to do that every time I do an install, so generally I just keep a wine menu next to my USP Menu, as they launch fine from the regular menu.

---

### Post by Malac on 2008-12-17
> **MetalHellsAngel said:**
> Well I currently run Guild Wars, Dreamweaver, Flash8, Fireworks 8, & The Macromedia Extension Manger Via Wine, those are pretty Much it. But none of them will launch via USP I can get them to work by using [this fix]("http://ubuntuforums.org/showpost.php?p=2175127&postcount=91") but it's a pain to have to do that every time I do an install, so generally I just keep a wine menu next to my USP Menu, as they launch fine from the regular menu.

If you could give me a copy of the .desktop files that you are using to launch these it will give me some real world cases to try and beat this bug into submission, it has been around far too long. If you could tar then attach to a post or via e-mail on USP About page that would be cool.

---

### Post by Ms_Angel_D on 2008-12-17
I would love to send these files to you but I'm not seeing them in my 

```
/usr/share/applications
```

Is there somewhere else where wine might keep these files. There is however a .desktop file called Wine Windows Program Loader I have zipped and attached it.

also here is the launch command from my menu editor, for launching Dreamweaver.

```
env WINEPREFIX="/home/angel/.wine/" wine "C:\Program Files\Macromedia\Dreamweaver 8\Dreamweaver.exe" 
```

I did note that in the post from my above link, there seems to be some issue with spaces. I'm not much of a programmer but this was mentioned in that thread. If there is anything else I can do please let me know.

Angel

---

### Post by collinp on 2008-12-17
Wine keeps its files in the directory .wine in your home folder.

---

### Post by Malac on 2009-02-11
I have committed a change to the application launching and .desktop parsing system which should solve this problem. SVN Rev #375.
Please can you let me know if this works as expected or throws up anymore errors.
Thanks.

---

### Post by Ms_Angel_D on 2009-02-24
Hi, sorry it's taken me a bit to reply, but I've not been well and hadn't felt like messing with any computer stuff lately. 

I have good news and bad news on this. First off the bad news, I did an upgrade and the problem persisted, wine programs still refused to launch through USP. 

Now the good news

For other reasons I decided to do a reinstall of ubuntu, which of course meant re-installing USP upon installation I have found that all wine software launches without a hitch through USP.

I'm not sure if I possibly upgraded incorrectly the first time or if there was something I missed. But I did want to say thanks for taking a look at this and fixing it, I really adore USP and am glad to have it.

---

### Post by Malac on 2009-03-12
Sorry I haven't replied for a while (busy as ever) :).
These updates required a reboot or maybe as you say something didn't get replaced that should have done, so maybe one of those was the problem.
Anyway I am glad it is working for you now.

---

