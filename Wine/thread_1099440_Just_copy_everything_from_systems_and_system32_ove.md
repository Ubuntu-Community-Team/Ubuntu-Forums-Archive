---
title: "Just copy everything from systems and system32 over. How does that sound?"
date: 2009-03-18
forum: Wine
---

### Post by amylase on 2009-03-18
Hi everyone.

More than once, in fact, twice, three times already have I resolved problems where programs apparently did't work in WINE initially, but worked after I found out and fed them a particular file or files they needed in c:\windows\system or c:\windows\system32.

For example, something wouldn't install. One way or another I figured out they needed some .DLL or whatever files in system or system32 folder. I copied that file over from my XP box to /c_drive/windows/systems or system32. Tried that software again and this time it worked. Usually it  would have wasted me a good hour or so but made me happy things actually worked.

I am just curious, what if I just copy all the files from my real Windows XP's systems and system32 directories, pour them into WINE's /c_drive/windows/systems or system32 directories once and for all. Maybe that'll make my existing Windows programs run with less glitches and allow more future programs to install without complaining about missing files.

Has anyone tried that already? or is there anything risky about doing this?

Thanks a lot. :popcorn:

---

### Post by Meow27 on 2009-03-18
it wont work,

---

### Post by alex.rayu on 2009-03-18
Sounds bad. If it were that easy everybody would just do it. It will not help you a bit.

---

### Post by hikaricore on 2009-03-18
no no no no no no NO

---

### Post by cogadh on 2009-03-18
Absolutely terrible idea. Some of the DLLs and such in system and system32 are completely not necessary to Wine, some of them will work worse than their counterparts already within Wine and still others are known to completely break Wine. You should only copy over and use specific DLL files, and that should only be done when a particular app calls for it.

---

### Post by amylase on 2009-03-19
Ok ok, I get the idea. I won't do it. :KS

---

