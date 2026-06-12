---
title: "Possible to restore old ~/.wine to new wine installation?"
date: 2010-05-03
forum: Wine
---

### Post by Kurtosis on 2010-05-03
I just did a clean install of Ubuntu 10.04, after having backed up my home directory from a prior installation.  I'd like to reinstall Wine, but don't want to have to reinstall all the programs from my prior Wine installation.

Is it possible to restore the old .wine folder, or the contents of the old .wine/drive_c/Program_Files, to the new Wine installation?

If I restore the old .wine to the home directory before reinstalling Wine, will the reinstall overwrite the old .wine and all my programs in it?  (I don't have room on the hdd for both ~/.backup/.wine and ~/.wine.)

---

### Post by asdfoo on 2010-05-03
> **Kurtosis said:**
> I just did a clean install of Ubuntu 10.04, after having backed up my home directory from a prior installation.  I'd like to reinstall Wine, but don't want to have to reinstall all the programs from my prior Wine installation.

Is it possible to restore the old .wine folder, or the contents of the old .wine/drive_c/Program_Files, to the new Wine installation?

If I restore the old .wine to the home directory before reinstalling Wine, will the reinstall overwrite the old .wine and all my programs in it?  (I don't have room on the hdd for both ~/.backup/.wine and ~/.wine.)


Installing wine doesn't touch .wine, .wine is only updated when you run wine.

If you have a new hdd (~/.wine doesn't exist), just

 mv ~/.backup/.wine ~/.wine

---

### Post by Kurtosis on 2010-05-03
Great, thank you!

---

