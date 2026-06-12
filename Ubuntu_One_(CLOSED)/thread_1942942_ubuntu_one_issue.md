---
title: "ubuntu one issue"
date: 2012-03-18
forum: Ubuntu One (CLOSED)
---

### Post by hunterkasy on 2012-03-18
I have 2 diffrent accounts with ubuntu one, I added the wrong computer to the wrong account, how can I connect the computer to the right account?

---

### Post by duanedesign on 2012-03-20
Running two accounts on the same machine can lead to errors(Root_Mismatch) with the different metadata from multiple accounts. The following steps will help make sure that does not happen.

1. Press Alt-F2, type "seahorse", press "Enter"

2. Right-click on any entries with "Ubuntu One" or "Desktopcouch" in the name and select "Delete"

3. Press Alt-F2, type "gnome-terminal", press "Enter" and then run:
```
u1sdtool -q
sudo rm -rf ~/.local/share/ubuntuone
u1sdtool -c

```
4. You should be prompted to enter your Ubuntu One login, be sure to use the Ubuntu One account you want to use.

---

