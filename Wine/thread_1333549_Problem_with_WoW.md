---
title: "Problem with WoW"
date: 2009-11-21
forum: Wine
---

### Post by Hmmster on 2009-11-21
Hi, 
A while ago i installed WoW, was downloaded & installed perfectly, but when i started patching problems appeared, at first i couldn't even open WoW, then i tried opening it through programs -> wine -> World of warcraft, wich worked... once, and after that it didn't work again.
I notice that i works after every time i run the blizzard repairer, but it just downloads the same patch..
I know there's probably another thread like this, but i prefer to get personal advice.
Sorry for my bad english, i am thirteen years old and live in finland, so i haven't learned so much.

---

### Post by Xog on 2009-11-21
Applications > wine > browse C:/

open Program Files

right click on the World of Warcraft folder, go to properties
enable all permissions where applicable to 'Create and Delete Files' and click enable permissions then click ok. you must do this after every update you do, or else linux will not let WoW.exe create files (which it needs to do to run) and it will not run.

---

### Post by Hmmster on 2009-11-21
That didn't change a thing.
EDIT: It appears that it will not save as that, when i click "Create and delete" It just resets to "nothing"
EDIT2: Okay, the folder in wine's C: Works to change fine, but the place i installed in doesn't work to change on.
EDIT3: But the launcher still won't open.. help. :)

---

### Post by Xog on 2009-11-21
> **Hmmster said:**
> That didn't change a thing.
EDIT: It appears that it will not save as that, when i click "Create and delete" It just resets to "nothing"
EDIT2: Okay, the folder in wine's C: Works to change fine, but the place i installed in doesn't work to change on.
EDIT3: But the launcher still won't open.. help. :)

don't use the launcher. open WoW.exe. and you have to click "Apply permissions to enclosed files" before clicking ok. if you click ok before you click Apply, it won't save.

---

### Post by Hmmster on 2009-11-22
I use wow.exe, but then the game starts up, the intro video plays and after that i get some error, or the comp freezes.

I did click that before.

---

### Post by Alatar1 on 2009-11-22
Try browsin on over to /home/username/.wine/drive_c/Program Files/World of Warcraft/WTF open the config.wtf folder and add this line to it ..

```
SET gxApi "opengl"
``` and see if that makes it work, this will tell the game to run in opengl mode

---

### Post by Hmmster on 2009-11-22
Um, 
Home -> Alex -> .wine -> drive_c -> program files ->
Here is common files and Internet Explorer
Common files -> Here's Blizzard entertainment
Blizzard entertainment -> Here's World Of Warcraft
World OF Warcraft -> Here's msvcr71.dll, unicows.dll, Uninstall.exe, Uninstall.xml

---

### Post by Xog on 2009-11-22
> **Hmmster said:**
> Um, 
Home -> Alex -> .wine -> drive_c -> program files ->
Here is common files and Internet Explorer
Common files -> Here's Blizzard entertainment
Blizzard entertainment -> Here's World Of Warcraft
World OF Warcraft -> Here's msvcr71.dll, unicows.dll, Uninstall.exe, Uninstall.xml

It seems you installed World of Warcraft under a different directory, not in your C:/ drive.
Where is WoW.exe located?

The folder that WoW.exe is located at is where the folder "WTF" will be. Inside the WTF folder will be Config.wtf. Open Config.wtf and add this to the bottom of the file:

```
SET gxApi "opengl"
```

---

### Post by Hmmster on 2009-11-22
I really seem to have scrwewed something up badly..
I installed it on my external harddive. But i have three Wtf folder, 
WTF.20091121-210851, WTF.20091121-202809 and just WTF
The first one contains:
Nothing
The second one contains:
RunOnce_WLK.wtf
The normal WTF one contains:
Nothing

Please, add [email]Alexanderi_@hotmail.com[/email] to MSN if you use that, so you could help me quicker. :P

---

### Post by Xog on 2009-11-22
> **Hmmster said:**
> I really seem to have scrwewed something up badly..
I installed it on my external harddive. But i have three Wtf folder, 
WTF.20091121-210851, WTF.20091121-202809 and just WTF
The first one contains:
Nothing
The second one contains:
RunOnce_WLK.wtf
The normal WTF one contains:
Nothing

Please, add [email]Alexanderi_@hotmail.com[/email] to MSN if you use that, so you could help me quicker. :P

reinstall world of warcraft onto your internal hard drive using wine 1.1.33 (which is also called 1.2)

---

### Post by Hmmster on 2009-11-22
Okay, so Xog explained to me via PM that i'm screwed. :/

---

### Post by petrocles on 2009-11-23
please explain how you are screwed?

---

### Post by Hmmster on 2009-11-23
[quote=Xog][quote=Hmmster][quote=Xog][quote=Hmmster][quote=Xog][quote=Hmmster][quote=Xog][quote=Hmmster][quote=Xog][quote=Hmmster]Add [EMAIL="Alexanderi_@hotmail.com"]Alexanderi_@hotmail.com[/EMAIL] so you can help me with the WoW prob quicker.[/quote]
add you to what[/quote]
Msn, if you use that.[/quote]
no i don't use msn. the problem is very straight forward and so is the answer. what problem are you experiencing now? Where is your WoW.exe located? You said you were opening the WoW.exe[/quote]
I have answered the question in the thread.[/quote]
Reinstall world of warcraft on to your internal hard drive.[/quote]
My internal harddrive is 20GB
Wow takes 17 GB with patches
3 GB left
Ubuntu takes about 3GB unpacked
0GB left

Stuff i need takes 5GB

-5GB left.
Sadface[/quote]

Then you can't play WoW.[/quote]
Why does it need to be on the internal?[/quote]

Because wine does not see your C:/ as your external drive. C:/ is part of your internal drive. Wine needs programs like this to be on C:/ in order to write files to it whenever it runs (like config.wtf)[/quote]
This.

---

