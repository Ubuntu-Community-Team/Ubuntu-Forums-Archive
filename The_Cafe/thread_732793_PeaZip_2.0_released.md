---
title: "PeaZip 2.0 released"
date: 2008-03-23
forum: The Cafe
---

### Post by Giorgio tani on 2008-03-23
PeaZip 2.0 was released friday: [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

This release introduces support for lpaq8 compression and for user-defined custom compression/extraction executables.
The new "Console" tab allows also to import as command line the job defined in the GUI frontend, and to edit, launch and save it; it comes expecially handy with custom archivers, allowing to adjust the syntax as needed beyond the capability of the frontend.
The UI was improved, with smarter context menus, more keyboard shortcuts and mouse functions (i.e. "extract selected files to..." invoked pressing spacebar or middle mouse button), and was fixed a bug that disallowed system benchmark function in previous releases.

---

### Post by madjr on 2008-03-23
very nice tool, gonna try and see whats new :)

---

### Post by Polygon on 2008-03-23
did you fix the font problem?

---

### Post by FuturePilot on 2008-03-24
I love this tool! Keep up the good work :guitar:

---

### Post by Polygon on 2008-03-24
the font issue has not been resolved...so i wont be using it. shame.

---

### Post by madjr on 2008-03-24
> **Polygon said:**
> the font issue has not been resolved...so i wont be using it. shame.

whats the font issue?

---

### Post by Giorgio tani on 2008-03-24
> **madjr said:**
> whats the font issue?

The latest stable version of Lazarus IDE which I use to write PeaZip don't allows to specify custom height for combobox menus in GTK1 and GTK2, so I can't resize them, or set the heigh variable, to fit the font size of some Linux distributions that uses a bit larger fonts, like Ubuntu does by default.

In this way the current value in comboboxes is readble on machines where small fonts are used, but practically unreadable on other ones where larger fonts are used, but if you click on them the strings in the dropdown menu are readable regardless the font size. Other GUI controls are fine.

I had not found a workaround for that issue, so I keep searching and hoping it will be fixed in the next release of the IDE.

---

### Post by bone2006 on 2008-04-03
Why isn't it in the repositories yet?  I love this applications, but when I go to another computer I forget to grab this file to install it, since 99.999% of the software I use comes from the repository.
What needs to happen for it to be put into ubuntu's repository?

Is it the license or something non-free? Would just love to have this in the repository

---

### Post by Polygon on 2008-04-03
someone has to provide a deb to the MOTU's (masters of the universe) and go through the process of getting it added to universe, and i guess that hasnt happened yet

---

### Post by bone2006 on 2008-04-03
What is generally the reason somebody hasn't done this yet?  Is it possible that the developer might not know the process? I know the website has the deb file, in which is what I used.

---

### Post by Giorgio tani on 2008-04-05
> **Polygon said:**
> someone has to provide a deb to the MOTU's (masters of the universe) and go through the process of getting it added to universe, and i guess that hasnt happened yet
I'll be glad to see PeaZip in Ubuntu repositories.
Can you suggest me the best way to get in contact with maintainers of repositories and suggest to test PeaZip for possible inclusion?

---

### Post by Polygon on 2008-04-05
this thread might help you

since i already think you know how to package it, there might be something on how to get it to the MOTU

[http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

---

