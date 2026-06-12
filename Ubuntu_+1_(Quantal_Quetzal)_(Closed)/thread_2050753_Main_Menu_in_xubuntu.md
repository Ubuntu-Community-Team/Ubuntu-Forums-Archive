---
title: "Main Menu in xubuntu"
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cgraham on 2012-08-31
Application menu in xubuntu 12.10 won't add new software installs and won't allow changes to main menu. Anyone else having this issue?

---

### Post by Elfy on 2012-09-01
There were some major changes recently - I knew that synaptic had disappeared. It's back now.

Create a bug report for it - with more detail about the issue so someone can verify it.

```
ubuntu-bug xubuntu-default-settings
```

Post the bug number here and I will if nothing else - check and me too it.

---

### Post by zaleksf on 2012-10-01
Running Xubuntu-12.10_64 on Dell Inspiron 1420...

I'm having the same issue - Main Menu editor app in the Settings Manager folder with take input, but will not create any new folders or menu items.

Is this eventually supposed to work, or should I install alacarte?

---

### Post by pqwoerituytrueiwoq on 2012-10-01
i know application installs work, and i can add new launchers via the gui
my base install was beta 2
if i try to make is show something that is in the settings editor it unchecks it 
if you copy the desktop from /usr/share/applications/ to ~/.local/share/applications/
it will probably let you edit it
you could copy everything to there like this 
[FONT=Courier New]cp /usr/share/applications/* ~/.local/share/applications/[/FONT]

---

