---
title: "How do you install DDO with wine?"
date: 2011-03-04
forum: Wine
---

### Post by skulkruncher on 2011-03-04
Hi, Ive have been reading around trying to find out if I can install DDO with wine or another method. However I am no tech wizard so if someone who has successfully installed DDO can tell me the precedure in simplest way, that would be much appreciated. I have read some helpful tutorials but im getting confused with all the things needed. So a simple guide would be best.

---

### Post by An Sanct on 2011-03-04
Here is the [WineHQ post]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2910"), looks good :) gold ratings everywhere. The post also includes installation details.

---

### Post by skulkruncher on 2011-03-04
Thanks, Hopefully i can get it working and dont mess it up. :)

---

### Post by skulkruncher on 2011-03-04
Ok i did almost everything right. I started to do the patching but at the end it said failed twice windows error somthing i forgot to write it down -.-. Also when i tried to start up the game it shows this message i have attached. Can someone please respond back and check what that might be?
I think i did something wrong in the patching process or i might not have gotten all the winetricks it needed. DDO started up normal without the patch so idk. Please help someone.

---

### Post by skulkruncher on 2011-03-04
im re patching it to c if that helps.

---

### Post by skulkruncher on 2011-03-04
ok this is what came up at end

EDIT: After installing vcrun2005 and 2008 i got this the 2 new pics

---

### Post by skulkruncher on 2011-03-04
dang so far Im getting frustrated becaue i think im making the problem worse by not knowing what to do. If anyone can figure the problem out please reply back.

---

### Post by An Sanct on 2011-03-05
You can get more detailed failure data, if you run the game in terminal
```
wine game_name.exe
```
Then please post the output (in "CODE" section, the **#** sign in the editor here).

---

### Post by Dustin2128 on 2011-03-05
You did get a copy of pylotro right? That's needed for running the game. As for the install, it's just a .NET downloader that doesn't work with wine for obvious reasons, you'll probably need to get some dotnet fixes from winetricks. That said, I usually just install it on a friend's windows laptop and copy the data over. Works like a charm with wine 1.3/pylotro. Not even much of a performance hit.

---

### Post by An Sanct on 2011-03-06
Well if you need windows mono libraries, it says so (wine complains) ... and if you don't need them, then it would be a waste of time, to install them. That is why I asked him to post the terminal output.

---

