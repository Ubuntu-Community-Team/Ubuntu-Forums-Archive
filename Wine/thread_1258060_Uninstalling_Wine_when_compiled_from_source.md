---
title: "Uninstalling Wine when compiled from source?"
date: 2009-09-04
forum: Wine
---

### Post by beastrace91 on 2009-09-04
So for a few days I was having issues compiled to the Wine repos so instead I just downloaded the source and compiled it from there - how ever I am now unable to uninstall said package... (sudo apt-get remove wine finds no installed packages as it was not installed as a deb) The Wine repos are now working for me again and I would like to install it from there, however the older version I have installed from source seems to be over writing the version I installed from the repos... How can go about removing the package I installed from source?

Thanks,
~Jeff

---

### Post by hikaricore on 2009-09-04
If you installed from source just goto your source directory and run:

> sudo make uninstall

IMHO you should always do this when installing from a package or an updated source.  :p
This doesn't affect your peronal .wine directory, just from running make install.

---

