---
title: "Cannot Change Default Path - Libreoffice"
date: 2013-01-18
forum: Ubuntu Development Version
---

### Post by Quarkrad on 2013-01-18
You cannot change the default path (Home/user) in Libreoffice (Tools/Options/Path).  I have installed Libreoffice 4 and the issue is still there.  I'm not sure this is a 13.04 issue specifically because it is also present in 12.10.  However, it is _not_ an issue on 12.04 or Windows (7).  It is a pity this issue is being carried over to 13.04 without being addressed. It looks to me something happened/broke in 12.10 and is still present in 13.

---

### Post by Quarkrad on 2013-02-04
bump

---

### Post by grahammechanical on 2013-02-04
I have not been able to edit the My Documents path for a long time. I test Ubuntu on one partition with my documents an another partition. The File Open dialog used to remember where I was getting my documents from. Even when I was opening them from another partition. Not any more. It always opens at /home/username.

This I would say is an issue with Libreoffice and not 13.04 specific.

Regards.

---

### Post by fantab on 2013-02-04
Yes this a an issue with Libreoffice, see **[this]("https://www.libreoffice.org/bugzilla/show_bug.cgi?id=55323")**. I have found the bug to be in package 'libreoffice-gnome'. 

There are two workarounds.

1. Remove pkg "libreoffice-gnome" and ~/.config/libreoffice and change the default save path of your choice... then reinstall "libreoffice-gnome". When you remove libreoffice-gnome you will loose Gtk theme and are left with 'ugly' theme. If yes then this workaround works.

2. Go to Tools- Options - General - Open/Save dialogs -> select/tick 'Use Libreoffice dialogs'. Now change the default save path.

In my 12.04 the only the first workaround, in 13.04 only the second method works....

Good Luck...

---

### Post by Quarkrad on 2013-02-04
I'm not qualified to say whether the issue is with libreoffice or the OS (ubuntu) but I can say that the version of LO (3.6) that has the bug is OK in win7.  The Beta version 4 also has the bug in Ubuntu but nort in win7.  I guess it is the Linux version of LO then.

---

