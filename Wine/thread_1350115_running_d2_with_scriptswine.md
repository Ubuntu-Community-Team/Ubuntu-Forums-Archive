---
title: "running d2 with scripts/wine"
date: 2009-12-09
forum: Wine
---

### Post by bizzy31 on 2009-12-09
I am pretty new to linux, and I cannot seem to figure out this problem.  I posted somewhere else on this site but i think it is better suited here.  Any input would be greatly appreciated.

[http://ubuntuforums.org/showthread.php?t=1349913](http://ubuntuforums.org/showthread.php?t=1349913)

---

### Post by Gary13579 on 2009-12-09
Hello, your thread should belong here. This is mostly a Wine related question.

Getting multiple D2 windows to work on bnet isn't an easy task, but it can be done. The problem is that battle.net stores Warden info in the file bncache.dat. If two windows are trying to use the same Warden module, when the server is asking for a different module... you'll drop out of the game in 45 seconds. This can be solved with symlinks.


Here is how I have done it.

First, run
```
gary@snuggles:~$ cd .wine/drive_c/Program\ Files/
```

Now, run
```
gary@snuggles:~$ mv "Diablo II" d1
gary@snuggles:~$ mkdir d2
gary@snuggles:~$ cd d2
```

You've now got two folders, d1 and d2. This is so each window can get it's own bncache.dat file, so Warden doesn't kill you.

Here's where it gets tricky. You need to copy the files d2char.mpq and d2sfx.mpq from d1 into d2.

```
gary@snuggles:~$ cp ../d1/d2char.mpq ./
gary@snuggles:~$ cp ../d1/d2sfx.mpq ./
```

These are the files that contain your cdkeys, so you must copy these over.

Now, it gets even more annoying. You need to make a soft symlink for every file in d1 into d2. you need to symlink ALL of the below files.
```
binkw32.dll   D2Direct3D.dll      D2sound.dll        
d2exp.mpq           d2speech.mpq       
Bnclient.dll  D2Game.dll          d2video.mpq        
D2Gdi.dll           D2VidTst.exe       
BNUpdate.exe  D2gfx.dll           D2Win.dll          
D2Glide.dll         D2xMusic.mpq      
D2Lang.dll          d2xtalk.mpq       
D2Launch.dll        D2xVideo.mpq             
D2MCPClient.dll     Diablo II.exe      
D2Multi.dll         Fog.dll
Game.exe           SmackW32.dll
ijl11.dll          Storm.dll
D2Client.dll  D2MultiRes.mpq
D2CMP.dll     d2music.mpq
D2Common.dll  D2Net.dll
d2data.mpq       
D2DDraw.dll   Patch_D2.mpq

```

So, for every file in that list, you need to run the following command:
[email]gary@snuggles:~/.wine[/email]/drive_c/Program Files/d2$ ln -s ../d1/file file

Say you are on the file Patch_D2.mpq, you need to run:
[email]gary@snuggles:~/.wine[/email]/drive_c/Program Files/d2$ ln -s ../d1/Patch_D2.mpq Patch_D2.mpq

IF THE FILE IS NOT IN THE LIST ABOVE, DO NOT SYMLINK IT. I have purposefully left out files that if symlinked (d2char.mpq, d2sfx.mpq, and bncache.dat) will screw things up.

Once you are done with that, you need to edit the cdkeys in d2. I suggest using a program like Onlyer's cdkey changer. Don't edit the d1 folder, just the d2 folder.

Then, the following:
[email]gary@snuggles:~/.wine[/email]/drive_c/Program Files/d2$ cd ~
gary@snuggles:~$ nano d1

and paste the following into it.

#!/bin/bash
wine explorer /desktop=d1,800x600 "C:\Program Files\d1\Game.exe"

hit control o to save, and control x to exit.

Then, run nano d2, and paste this into that:


#!/bin/bash
wine explorer /desktop=d2,800x600 "C:\Program Files\d2\Game.exe"

Control o, control x.

Now, run:
gary@snuggles:~$ chmod +x d1
gary@snuggles:~$ chmod +x d2


and you can use multiple cdkeys!

---

### Post by bizzy31 on 2009-12-09
hey thanks a lot for replying, but the "~$" command doesn't seem to be working.  i'm not supposed to put "gary@snuggles" right?  

this is the guide i was following, he seems to need a lot less work to make it work, but i have no idea what he is telling me to do.
[http://diablo.incgamers.com/forums/showthread.php?t=732636](http://diablo.incgamers.com/forums/showthread.php?t=732636)

---

### Post by akoskm on 2009-12-09
Do not include the **gary@snuggles:~$** part of the commands.

ps.:It indicates the current user at host. When you open your gnome-terminal you'll see  your own user @ host.

---

### Post by bizzy31 on 2009-12-09
> **akoskm said:**
> Do not include the **gary@snuggles:~$** part of the commands.

ps.:It indicates the current user at host. When you open your gnome-terminal you'll see  your own user @ host.

ah ok, i realized that after a while but when i type in the first line, it says no such directory or file exists (i changed the c to g, as well as the folder name to "programs"). 

i was also wondering whether there is a way to assign drives with a letter.  in windows it shows up as G: but in ubuntu it's labeled as a huge string of numbers and letters.

---

### Post by akoskm on 2009-12-10
> **bizzy31 said:**
> ah ok, i realized that after a while but when i type in the first line, it says no such directory or file exists (i changed the c to g, as well as the folder name to "programs"). ...
Which command returns the "no such file or directory" message?

> **bizzy31 said:**
> 
...i was also wondering whether there is a way to assign drives with a letter.  in windows it shows up as G: but in ubuntu it's labeled as a huge string of numbers and letters.

You can create custom drives in wineconfig under the Drives tab. Open the terminal and start it with
```

winecfg

```.

---

