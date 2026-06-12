---
title: "Wine Tricks: MS Visual C 2005 Runtimes (Warcraft 3)"
date: 2009-02-11
forum: Wine
---

### Post by dethredic on 2009-02-11
Ok, so I am trying to get warcraft 3 to work. It installed fine, but then when I went to play the game, it said it couldn't find the cd (even though it is in) I head over to the wineHQ site ( [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126) ) and sure enough it says i will get the error unless I install: MS Visual C 2005 Runtimes with wine tricks.

So I download the winetricks, but I am looking down the list of programs you can install, and "MS Visual C 2005 Runtimes" is not on the list. There are some MS Visual C++ libraries, but those didn't help.

So either I am missing something that is obvious, or someone screwed up...

EDIT: I installed everything that started with Microsoft Visual and it still doesn't work.

EDIT: I just went and downloaded the file from the M$ site:
[http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647)

I then did "wine vcredist_x86.exe". The error still occurs. :(

---

### Post by Dizzle7677 on 2009-02-12
It's vcrun2005 in winetricks.

Better off deleting the .wine directory and try the vcrun install again unless you have alot of stuff in Program Files,etc & in the registry...Reinstall warcraft after vcrun.

EDIT: It's actually vcrun2005 & vcrun2005sp1. Install one and then the Sp1 , not both together. You still may need to delete the /home/(user)/.wine directory if that doesn't do the trick and then do the vcrun installs.. No need to reinstall the program.

---

### Post by binbash on 2009-02-12
Yes it is vcrun2005 and dont forget to rename the movie folder after installation (also dont forget to add -opengl when launching the game.Example : wine asdasd.exe -opengl)

---

