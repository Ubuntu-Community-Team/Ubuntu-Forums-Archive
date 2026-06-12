---
title: "mupen64plus m64py keeps crashing"
date: 2018-03-25
forum: Ubuntu/Debian BASED
---

### Post by spyrofan9890 on 2018-03-25
i'm running Bodhi 4.5.0 32bit system

i try to setup mupen64plus it keeps crashing when i try to setup the library path  libmupen64plus.so.2 it keeps giving me this error or what ever this is the log
-------------------------------------------------------------------------------------------------
Error Signal Information:
    m64py  was interrupted by an Abort Signal.


Output Data:
    There was no output


Error Logs:
    There was no error message
-------------------------------------------------------------------------------------------------

what i'm i doing wrong?

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **Ubuntu/Debian BASED, a more appropriate forum**.*

---

### Post by spyrofan9890 on 2018-03-26
never mind i found the problem.

---

### Post by wildmanne39 on 2018-03-26
Would you please post the solution for the good of all the people that encounter the same problem.

Thanks

---

### Post by spyrofan9890 on 2018-03-26
yeah sure sorry about that

for people that were having this error m64py was interrupted by an Abort Signal when you try to browse to library file you get the error m64py was interrupted by an Abort Signal there a fix i found

[COLOR=#000000]don't browse the path since it will crash the emulator when choosing the file instead copy the path to the file remember to not click browse or it will crash here the path for 32bit systems 

[/COLOR]library file
/usr/lib/i386-linux-gnu/libmupen64plus.so.2.0.0


plugins directory
/usr/lib/i386-linux-gnu/mupen64plus

data directory
/usr/local/share/mupen64plus

roms directory
were your roms are

once done close the emulator and reboot your computer once your back open the emulator again and now you can setup the emulator 
if you get an error when opening a rom from list instead open it from manually it should work now

---

