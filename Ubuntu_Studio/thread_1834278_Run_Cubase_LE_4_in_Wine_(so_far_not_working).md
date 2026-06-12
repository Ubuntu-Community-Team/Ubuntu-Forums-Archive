---
title: "Run Cubase LE 4 in Wine??? (so far not working)"
date: 2011-08-27
forum: Ubuntu Studio
---

### Post by youWho on 2011-08-27
Hi all,

I got a copy of Cubase LE 4 for Windows along with a small recorder I bought and I'd like to try running it with Wine, but so far I haven't been able to download the license for Cubase. I managed to get all the way through getting an "activation code" but then in the Syncrosoft "License Download Wizard" that comes with Cubase LE 4 when I enter that "activation code" and try to go to the next step---downloading the license---where it says "Select Target eLicenser" it says "No licenses found" and the "Next" button is grayed out and I'm stumped. I don't know if anybody has tried this and gotten it to work all the way through, but if so if you could please tell me how you did it I'd appreciated it (THANKS).

I'm using Ubuntu Studio Natty 64 bit.

The copy of Cubase LE 4 came with an Olympus LS-10 by the way, and it's legally mine and all, if you wanna know.

Thanks.

---

### Post by sgx on 2011-08-27
Hi, it's probably not going to work. Reaper works wonderfully well,
and it's set up requires no activation or copy protection. After
a trial period, the honor system is employed, $40 fee for those
earning less than $20,000 a year in music production. There are
no linux equivalents yet. To use windows vst plugins in reaper,
you'll need to install wineasio, and run the command 

regsvr32 wineasio.dll 

Cheers

(sometimes a windows custom installer pops up a window behind other open windows, so minimize or drag the open windows in case a requestor window
is lurking. Also, try running the installer from the terminal, as missing
.dll files will sometimes be reported in the terminal output, and you can
download them and put them in

.wine/drive_c/windows/system32

This topic may help:

[http://www.cubase.net/phpbb2/viewtopic.php?p=704107](http://www.cubase.net/phpbb2/viewtopic.php?p=704107)

C: in wine is .wine/drive_c   you may need to delete 2 syncrosoft
folders after each install attempt

---

