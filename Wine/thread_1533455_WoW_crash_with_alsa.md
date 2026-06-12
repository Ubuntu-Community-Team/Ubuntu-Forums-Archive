---
title: "WoW crash with alsa"
date: 2010-07-18
forum: Wine
---

### Post by totalSKID on 2010-07-18
OK so I have successfully installed world of warcraft using wine and have been able to login and select a character.  problem happens when the world loads; everything loads fine and works for 3-10 seconds then it crashes.   
The screen goes black (giving a no input message) and the computer keeps running but the audio stops a min after the screen goes black.  I think it is called hard locking.

anyway I tried all the 'crash after loading' bug fixes and none seemed to work.  So then I go into the wine config audio drivers and uncheck alsa.  Bam, WoW runs fine now!  Only problem is that I have no more audio; tried checking OSS driver but that doesnt work either.  

If anyone knows how to either fix the alsa problem, or get oss to work it would be greatly appreciated.
Thanks in advance

---

### Post by asdfoo on 2010-07-18
> **totalSKID said:**
> OK so I have successfully installed world of warcraft using wine and have been able to login and select a character.  problem happens when the world loads; everything loads fine and works for 3-10 seconds then it crashes.   
The screen goes black (giving a no input message) and the computer keeps running but the audio stops a min after the screen goes black.  I think it is called hard locking.

anyway I tried all the 'crash after loading' bug fixes and none seemed to work.  So then I go into the wine config audio drivers and uncheck alsa.  Bam, WoW runs fine now!  Only problem is that I have no more audio; tried checking OSS driver but that doesnt work either.  

If anyone knows how to either fix the alsa problem, or get oss to work it would be greatly appreciated.
Thanks in advance

which version of wine are you using? most recent is wine-1.2

open a terminal and type 'wine --version' to find out

if it still crashes with the most recent version, suggest you post a log [http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by totalSKID on 2010-07-18
using 1.1.42
I uninstalled it then entered sudo apt-get install wine1.2 in the terminal but it just reinstalled 1.1.42 
am i doin it wrong?

---

