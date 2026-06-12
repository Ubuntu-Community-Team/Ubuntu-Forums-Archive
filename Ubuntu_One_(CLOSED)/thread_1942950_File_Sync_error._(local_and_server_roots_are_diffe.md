---
title: "File Sync error. (local and server roots are different (ROOT_MISMATCH))"
date: 2012-03-18
forum: Ubuntu One (CLOSED)
---

### Post by hunterkasy on 2012-03-18
File Sync error. (local and server roots are different (ROOT_MISMATCH))

how do I fix it?

---

### Post by PaulW2U on 2012-03-18
Presumably [https://one.ubuntu.com/help/faq/what-does-the-root_mismatch-error-mean/](https://one.ubuntu.com/help/faq/what-does-the-root_mismatch-error-mean/) contained the answer you were looking for.

---

### Post by duanedesign on 2012-03-20
This happens when running two accounts on the same machine. The following steps will help clean this up.

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

### Post by guindasoft on 2012-05-10
> **duanedesign said:**
> This happens when running two accounts on the same machine. The following steps will help clean this up.

1. Press Alt-F2, type "seahorse", press "Enter"

2. Right-click on any entries with "Ubuntu One" or "Desktopcouch" in the name and select "Delete"

3. Press Alt-F2, type "gnome-terminal", press "Enter" and then run:
```
u1sdtool -q
sudo rm -rf ~/.local/share/ubuntuone
u1sdtool -c
```4. You should be prompted to enter your Ubuntu One login, be sure to use the Ubuntu One account you want to use


Thank you very much.

---

### Post by Farbror on 2012-11-14
THANX! Lovely with people who know what they are doing. Now, I can continue working from home without the USB.

/J

---

### Post by greggc2006 on 2013-02-07
> **duanedesign said:**
> This happens when running two accounts on the same machine. The following steps will help clean this up.

1. Press Alt-F2, type "seahorse", press "Enter"

2. Right-click on any entries with "Ubuntu One" or "Desktopcouch" in the name and select "Delete"

3. Press Alt-F2, type "gnome-terminal", press "Enter" and then run:
```
u1sdtool -q
sudo rm -rf ~/.local/share/ubuntuone
u1sdtool -c
```

4. You should be prompted to enter your Ubuntu One login, be sure to use the Ubuntu One account you want to use


Thanks so much, its always a relief to come across simple instructions that work!!

---

### Post by RustyHammer on 2013-03-18
Thank you so freaking much!

---

### Post by fsopho on 2014-02-17
Txs so much! :KS

---

