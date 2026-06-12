---
title: "UT2004 installation issue"
date: 2007-09-25
forum: Ubuntu Gamers Arena
---

### Post by qabach on 2007-09-25
When I try to install Unreal Tournament 2004 (CDs) I get an error for which I haven't been able to find a solution online.

I made a local copy of linux-installer.sh, set its permissions to 755, and then double-clicked on it, the text editor (gedit) tried to open it and I got an error which said "Could not open the file /home/qabach/linux-installer.sh. gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again."

The two options in the drop-down were UTF-8 and ISO-8859-15, both of which I tried, but neither worked. Does this file use some other kind of encoding? Do I have another problem here?

Any help is appreciated.  I am very new to Linux, so I won't be surprised if I'm missing something obvious.

---

### Post by Perfect Storm on 2007-09-25
```
cd <distination>
sudo sh linux-installer.sh

```

---

### Post by Lord Illidan on 2007-09-25
You are trying to read the program, which is in binary format (hence, you cannot edit it with a text editor). What you want to do is **run** the program.

You can double click it, and select Run.

---

### Post by qabach on 2007-09-25
That is just my problem. Normally, I would choose "run" when prompted, but there is no such prompt for this file.
It is possible that there is a file-type-specific setting I would need to change.

Edit: Artificial Intelligence's suggestion of specifying the program to run it with worked (thanks.) I'll try associating the filetype with that operation later.

---

