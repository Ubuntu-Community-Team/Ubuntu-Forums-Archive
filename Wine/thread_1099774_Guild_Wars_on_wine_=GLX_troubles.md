---
title: "Guild Wars on wine =GLX troubles"
date: 2009-03-18
forum: Wine
---

### Post by rasmus91 on 2009-03-18
Hi

Yeah, I'm Experiencing problems running Guild Wars, and thats one of the games that should work best with wine...

Okay, here was my terminal output, it actually launched, and asked me where to download updates to. (set the installation folder but the entire game was there, so it wasn't an installation)

I used the terminal, and my output is as follows:

( i've heard others having some problems that looked terribly much alike. if anyone has an idea on how to solve, please tell me. I would LOVE to be able to play Guild Wars again! )

```
rasmus@rasmus-Dell-E6400:~/.wine/drive_c/Program Files/Guild Wars$ wine Gw.exe
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:EnumDisplayDevicesW ((null),0,0x32eb54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e258,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc58,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dce8,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com" 0x147868 0x15bdea4
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com/support/support.html" 0x14dde8 0x15bdea4
fixme:shell:DllCanUnloadNow stub
rasmus@rasmus-Dell-E6400:~/.wine/drive_c/Program Files/Guild Wars$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  481
  Current serial number in output stream:  481


```
Should be said that i've tried almost as much as everything it said on the winehq page, and its like it didn't work...
i can see that there are also some sound problems, but ithink they should be minor, however a solution for those are welcome as well.
Please give some help if you have any idea on how to solve.

Thank you for your time and effort :)
Running ubuntu 9.04       wine version 1.1.17 (i think) (graphic card intel 4500... yeah i know...)

Maybe i should just add, that after the above one i tried to run in a emulated desktop, and without, When i launch with emulated desktop with terminal, output is:

```
rasmus@rasmus-Dell-E6400:~$ wine .wine/drive_c/'Program Files'/"Guild Wars"/Gw.exe
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  488
  Current serial number in output stream:  488

```

i get the same thing when i try doing it while its not set to windowed. while double clicking made my screen black, made it flash, and returned me to the Ubuntu login page. it doesn't do that anymore

---

### Post by hikaricore on 2009-03-18
Run this from a terminal:

> glxinfo | grep rendering

If it returns a no, hunt around the forums for info on setting up your intel video drivers properly.

---

### Post by rasmus91 on 2009-03-18
It returns me a no:

```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

I'll try tracking down an answer. But if anyone has any ideas, tell me what to do, I'm all ears!

---

