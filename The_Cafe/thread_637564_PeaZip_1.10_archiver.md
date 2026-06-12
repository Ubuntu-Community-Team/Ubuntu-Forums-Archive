---
title: "PeaZip 1.10 archiver"
date: 2007-12-11
forum: The Cafe
---

### Post by Giorgio tani on 2007-12-11
Hi, I'm glad to announce PeaZip reached 1.10 release: [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

PeaZip 1.10 is compiled with new Lazarus release, 0.9.24, which allows to resolve visualization issues previously seen on GTK2.
Now PeaZip precompiled for GTK2 it should be rendered correctly on all Linux distributions, I tested it positively on Ubuntu 7.10 [http://sourceforge.net/project/screenshots.php?group_id=178996&ssid=72882](http://sourceforge.net/project/screenshots.php?group_id=178996&ssid=72882) (one issue still: with some fonts the combobox height may be too small, I'm working on it for future updates)
However, all packages of the program (installable DEB, RPM and TGZ; standalone TAR.GZ) are available also precompiled for GTK1 widgetset for people needing or preferring GTK1 applications.

In this release it was also introduced drag and drop from system to the application (the vice-versa is not jet implemented): you can open archives and add objects to archive layout or to existing archives dragging files and folders to the application.

I hope the new release of PeaZip may be useful for many Ubuntu users!

---

### Post by janfsd on 2007-12-20
Just tried it now, thanks for fixing the visualization problem. This program is great, I think I will make it the default for handling compressed files.

However I think there is still a bug when trying to change the theme. It gives this error:
```
Cannot save configuration file, check if the path is writeable...
```
I suppose it happens because of the location of the conf.txt file, and to edit that it requires root privileges. I just change it by manually modifying it. But maybe you can fix it in the next release? Anyway thanks for your effor on making this program.

---

### Post by XVampireX on 2008-01-03
Hi, I'm having a little problem with peazip, check the attachment, you'll know what I'm talking about in an instant

Also it would be really nice to eventually see some information on the progress of the compressing/decompressing of an archive...

---

### Post by janfsd on 2008-01-06
> **XVampireX said:**
> Hi, I'm having a little problem with peazip, check the attachment, you'll know what I'm talking about in an instant

Also it would be really nice to eventually see some information on the progress of the compressing/decompressing of an archive...
The fonts problem is still an issue as the author said in the 1st post, he says he is working on that. As for the progress, go in to options and in general behaviour tab look at the option: binaries user interface, check on console for more detailed information...

---

