---
title: "Ubuntu 12.04 Ubuntu One"
date: 2012-03-14
forum: Ubuntu One (CLOSED)
---

### Post by dh04000 on 2012-03-14
I'm getting an error message and no syncing. The message is 

File Sync Error (local and server roots are different (ROOT MISMATCH))

Is everyone on 12.04 beta experiencing this, or did something else happen during my installation?

Thanks

---

### Post by dh04000 on 2012-03-17
Bump

---

### Post by dh04000 on 2012-03-17
Never mind, the answer was here.


[https://one.ubuntu.com/help/faq/what-does-the-root_mismatch-error-mean/](https://one.ubuntu.com/help/faq/what-does-the-root_mismatch-error-mean/)

---

### Post by duanedesign on 2012-03-20
The formatting on the FAQ is kind of hard to read right now. Something that is being worked on. In the meantime I thought i would post the steps here for resolving the Root_Mismatch error.
It is always a good idea to have your data backed up.

1. Press Alt-F2, type "seahorse", press "Enter"

2. Right-click on any entries with "Ubuntu One" or "Desktopcouch" in the name and select "Delete"

3. Press Alt-F2, type "gnome-terminal", press "Enter" and then run:
```
u1sdtool -q
sudo rm -rf ~/.local/share/ubuntuone
u1sdtool -c
```

4. You should be prompted to enter your Ubuntu One login, be sure to use the Ubuntu One account you want to use

---

