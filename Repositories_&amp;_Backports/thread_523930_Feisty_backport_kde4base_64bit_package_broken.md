---
title: "Feisty backport kde4base 64bit package broken"
date: 2007-08-12
forum: Repositories &amp; Backports
---

### Post by 5ER on 2007-08-12
Title says it all and yeah I'm sure.

Adept says "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages." while installation and if I check the package status in Adept, it says "BROKEN (installed)"

Some kde4 programs are missing and some of those which aren't missing, miss something else. For example, there is a section of options in dolphin completely blank.

Where can I report it?

One of the problems is that kdelibs5-data and kde4base-data both contain file "/usr/lib/kde4/share/apps/kdeprint/filters/enscript.desktop". And it comes to an error when it tries to overwrite. Is there any way to remove this file from the package or install the package without this file? Maybe it's the only problem.

---

### Post by 5ER on 2007-08-14
Woo hoo, I used --force-overwrite option in dpkg and now it works!

---

### Post by Clay_Banger on 2007-08-15
im having the same problem, but am unsure of when to put the --force-overwrite in... can you provide more info on it please?

---

### Post by 5ER on 2007-08-15
Before you do anything, make sure you removed all kde4 related packages (kdelibs5, kdelibs5-data, kdepimlibs5, kdepimlibs5-data, kde4base, kde4base-data and development packages).

Sure, first download the packages needed (or only kde4base-data).
Then install kdelibs5, kdelibs5-data, kdepimlibs5, kdepimlibs5-data. I downloaded them and installed them with kpackage, cause I had some problems with adept and similar programs.
Then you have to install kde4base-data: run```
sudo dpkg --force-overwrite install /path/to/kde4base-data.deb
```
After that you only have to install kde4base.

You can get some packages in /var/cache/apt/archives/ if you were already trying to install kde4. That's the directory where adept and similar programs download packages before they install them.

---

