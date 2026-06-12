---
title: "HowTo remove entries from lightdm"
date: 2013-05-10
forum: Tutorials
---

### Post by sp-1070 on 2013-05-10
If your anything like me and keep searching for that one perfect window manager you might end up with some entries in lightdm that are broken.

example : i had installed KDE-plasma desktop and upon purging it the entries remained in lightdm of course giving an error upon trying to log into it.
Also if you use something else then gnome or the ubuntu one you can remove them without actually breaking your system somehow.

So first of all lightdm's entries are a serie of links or files in the directory /usr/share/xsessions

lightdm reads these entries and puts them in the list, all of these files end with .desktop if it doesn't have that extension lightdm wont put it in.
So as example we take gnome.desktop and ubuntu.desktop

As i use cinnamon i don't really need them but i won't throw them away because if cinnamon breaks il have a failsafe, so all i will do is rename them.

First we open a terminal and navigate to /usr/share/xsessions

```
cd /usr/share/xsessions
```

now well rename them using the command mv

```
sudo mv ubuntu.desktop ubuntu.desktop.old && sudo mv gnome.desktop gnome.desktop.old 
```

Upon re-logging into the system the entries gnome and ubuntu are gone.

Hope it helps See ya

---

