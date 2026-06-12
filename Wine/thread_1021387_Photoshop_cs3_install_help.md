---
title: "Photoshop cs3 install help"
date: 2008-12-25
forum: Wine
---

### Post by SonnHalter on 2008-12-25
ok i have the cd loaded. i went to the cd browser-adobe cs3 and right clicked "setup.exe" chose "open with wine program loader"

and then nothing happens. nothing. 


help?

---

### Post by alex.rayu on 2008-12-25
I made sure it was set to report itself as windows XP and traced it to where it exited with the error 
```
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
```

---

### Post by alex.rayu on 2008-12-25
Guess what! After removing Winetricks (removed the whole .wine folder) - it installed.

UPD: I have been too hasty. Could not repeat. I have compiled wine 1.1.11 and will now retry.

---

### Post by alex.rayu on 2008-12-25
I have been too hasty. Could not repeat. I have compiled wine 1.1.11 and will now retry.

UPD: Install failed after installing Shared Components just before installing the Photoshop proper - even with 1.1.11 - I had to install msxml3, gdiplus and gecko though.

I am totally lost as for why I succeeded once and that with with 1.1.10
Anybody expert here?

---

### Post by SonnHalter on 2008-12-25
how'd u get 1.1.11?

---

### Post by alex.rayu on 2008-12-25
From Wine-HQ sources and compiled.

---

