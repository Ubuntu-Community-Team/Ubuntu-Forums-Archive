---
title: "Unable to play some WAV files"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by sting3r on 2010-01-25
Hi Everyone,

I just installed Fruity Loops 7 Studio (wine) on my laptop and noticed that I can play pre-made songs but not getting sound when I trying to create a new one. After looking into it I noticed that I can open and use some samples but not all of them.. I then noticed when browsing to the sample directories, I'm able to open only some WAV files. the other give me a message: Could not decode stream. I forward one of this file to a friend that also using KDE and he was able to open it with no problem..

Does anyone have an idea of why I can only execute certain WAV file while the other fail?

any help will be appreciated,

Thanks,

Soos

---

### Post by sgx on 2010-01-26
Hi, it may be a quirk in the sampling process, try importing one of the duds in audacity and rezound, and export it as a .wav again, and make
sure there are no special characters in the filename. (when running a linux command in wine, a space must be filled with a *    for example

wine /home/user/.wine/drive_c/Program*Files/reaper/reaper.exe

If reconverting/resaving are successful, you could probably batch convert a folder of duds using ffmpeg and a wildcard. Google always has ffmpeg command strings for common procedures.
Cheers

---

### Post by sting3r on 2010-01-26
Thanks SGX!

I'll give it a shot when I'm back from work.. Hopefully that will do it so I can finally :guitar: on my K 

Thanks,

Soos

---

