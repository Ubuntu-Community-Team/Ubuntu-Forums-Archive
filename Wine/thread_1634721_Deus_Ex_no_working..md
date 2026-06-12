---
title: "Deus Ex no working."
date: 2010-11-30
forum: Wine
---

### Post by laagamer on 2010-11-30
Hey, I'm trying to run the game Deus Ex through Wine 1.3.4. I have everything installed okay and I don't get any errors, but when I play the game it doesn't work. The screen turns black then keeps flashing my desktop with what looks to be the mouse cursor from the game except everything is all distorted, messed up, and blinking randomly. 

I have wine config changed to OSS and Emulator like several people said which did actually get the sound to work. I have tried to follow the directions linked here: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775)

I followed step 6 and pasted exactly what was given below it in order to run the game without the disk, which works briefly for about 30 seconds before crashing. I think I did this correctly though because the game does run for a short time, so I don't think the crash has anything to do with lack of disk. 

Also I have completely no idea how to do step 7. I followed the link and read the instructions (at least I think they were) but they might as well have been in Chinese.  Could this possibly be the problem? I don't have any of the game even appear. Not a rapid version of the game as people describe. Just my distorted desktop flashing. That leads me to think this may not be the cause either.

Either way does anybody know how to fix the screen flashing, game not showing and not working or at least what the problem might be?

---

### Post by cogadh on 2010-12-01
Sounds like it could be a video card/driver issue. Hardware specs?

---

### Post by bobwyajnr on 2010-12-04
Deus Ex should work very well in Wine (since it only uses DX7). 

Can we get your hardware specification (especially the graphics card - which I presume is ATI or Intel!!) ??

If you post on these forums and don't respond to follow-up questions for 3 days then your post will get buried under the avalanche of new posts!! Not a good plan :rolleyes::rolleyes:

Can you try running Deus Ex in a BASH console to see any error messages that Wine is outputting? I can talk you through this if you are unclear what to do... It will be something _similar to_:```

cd ~/.wine/drive_c/DeusEx/
wine DeusEx.exe
```typed at the command line.

Bob

---

### Post by laagamer on 2010-12-10
Bash console?

Um sorry guys I don't really know the specs on this one. T_T 

Basic Dell Inspiron 1501 thats about 3-4 years old. 



I actually got it kind of working. 

I did completely nothing. 

Just booted it up and ran the game and it worked all of a sudden. Only problem is occasional sped-up gameplay but thats because of the dual core processor as I recall? Theres a way to fix it but I'm not that good with a computer and a simple reboot fixes the problem. lol

Either way I still don't understand why the graphics look twisted and morphed around the edges. T_T

I'll live though and thanks for the replies.

Oh ya and OSS sound with full graphics and running on Windows XP for wineconfig. 

Also I did not install DirectX and I'm using that openGL or whatever its called.

And I have no idea what in the heck I just said. =D

---

