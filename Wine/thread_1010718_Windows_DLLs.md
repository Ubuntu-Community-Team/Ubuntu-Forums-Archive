---
title: "Windows DLLs"
date: 2008-12-14
forum: Wine
---

### Post by Eddie002Fast on 2008-12-14
I was wondering if anyone knew where i could go to obtain a list of all the Window's DLLs so i could Insert them into Wine ! Any feedback would be great thx!

---

### Post by jrusso2 on 2008-12-14
Actually you don't want all of them.  Certain of the WINE DLL's need to remain the WINE version or it won't work.  Just add the Windows DLL's you need when you install an  app that requires it.

---

### Post by 3rdalbum on 2008-12-14
Do a search on Google for "find Windows DLL" and you'll find many exhaustive lists.

---

### Post by Eddie002Fast on 2008-12-14
Thank You guys very much that was hepful and i didnt even think of it like that. Your right Wine has its own DLLs so i might not need all of window DLLs i might only need 1 or 2 or something thx !!!:lolflag:

---

### Post by soluphobe on 2008-12-14
Just look in C:\WINDOWS\system32 for the dlls you currently have - AFIAK all dlls windows (and installed software) wants are stored there.  Of course, there is no list of 'all' dlls because some 3rd-party software installs its own, and then you start getting into different concurrent and conflicting versions of the same dll (trust me - its messy).

But, as others have said, you should only grab the ones you need when you need them.

---

### Post by Eddie002Fast on 2008-12-14
I know this might be a little off topic but i just noticed something i have typed in posts/threads thx or thank you or thanx or thanks before and it isnt showing up on my stats.....i noticed your guys stats below your Avatars...........How you guys thank people and get it too post in ur stats i mean i dont want everyone thinking i never thank people LOL...any help would be greatly appreciated !!!  :D

---

### Post by Eddie002Fast on 2008-12-14
nvm there is a thank button on the bottom right corner of peoples posts LOL I just figured it out after I posted LOL =D

---

### Post by merlyn on 2008-12-14
While on the subject of Windows DLLs for Wine.

If you find that a newly installed app fails to run, attempt a launch via the command line.

Doing it this way will provide visual feedback, (text) of any errors that are occurring including the names of any DLLs that are required.

Cheers.

---

