---
title: "Granddaughter reinstalled Windows7 over in-use Windows7 system"
date: 2013-10-16
forum: Windows
---

### Post by KWLLC on 2013-10-16
Samone did an install over MorMor's PC with all her students' evaluations coming up. I know that previous versions only did a 'quick' format by finding a vacant block on the hard drive to serve as a new directory root and overwriting the MBR with that address. If that is still true, then the previous directory tree could still be intact. Correcting the MBR *should* then allow me to reconnect the previous tree to Windows and 'heal the breach'. Would this work and if so, is there a HDD reader available in Linux to help me find the lost root address?

---

### Post by CharlesA on 2013-10-17
Depending on how they installed, there should be a windows.old folder in the C drive. Otherwise, data recovery might be your only option.

I would use a *nix live cd and mount the drive read only to take a look, so nothing is written to it.

---

### Post by SeijiSensei on 2013-10-17
I would also encourage "MorMor" to back up her files regularly.

---

### Post by kurt18947 on 2013-10-17
> **CharlesA said:**
> Depending on how they installed, there should be a windows.old folder in the C drive. Otherwise, data recovery might be your only option.

I would use a *nix live cd and mount the drive read only to take a look, so nothing is written to it.

Oohhhh yeah.  Something like the Windows equivalent of Lucky Backup takes seconds to run and can save mucho angst.  Flash drives are cheap.

---

