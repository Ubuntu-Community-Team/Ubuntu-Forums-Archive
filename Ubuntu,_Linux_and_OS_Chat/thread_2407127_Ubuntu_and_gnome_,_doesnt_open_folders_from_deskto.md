---
title: "Ubuntu and gnome , doesnt open folders from desktop"
date: 2018-11-30
forum: Ubuntu, Linux and OS Chat
---

### Post by radgezito on 2018-11-30
I use ubuntu 18.10 with gnome 3.28 and I have the following problem, on the desktop I have different types of files, txt, pdf and these open perfectly with the default program.

The problem I have when trying to open a folder does nothing, it does not give an error but it does not open it either.

What I can do?
Thank you

---

### Post by Ars_Ivci on 2018-11-30
I am unable to replicate your problem (running Unity on 18.10, files 3.26.4). Just curious, what is your files/nautilus version?

---

### Post by Ars_Ivci on 2018-11-30
Maybe this thead can shed some light:
[https://community.ubuntu.com/t/nautilus-3-30-status/8907](https://community.ubuntu.com/t/nautilus-3-30-status/8907)

---

### Post by radgezito on 2018-11-30
> **Ars_Ivci said:**
> Maybe this thead can shed some light:
[https://community.ubuntu.com/t/nautilus-3-30-status/8907](https://community.ubuntu.com/t/nautilus-3-30-status/8907)
[COLOR=#212121][FONT=arial]
[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]The problem I have is that I have "X" folders on the desktop and if I press double click the folder does not open, if I do the right button of the "open" roton, it does not do anything either.


I have another option that is to open a "nautilus" go to the desktop folder and there if it opens ... but it is not the solution I'm looking for.

Thank you

[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-11-30
Check that the folders on the desktop have execute permissions enabled with ```
ls -la Desktop
```

Folders **must have execute** permissions enabled to be able to work properly as folders.
See the old (2009) but still relevant thread at [https://ubuntuforums.org/showthread.php?t=1288807](https://ubuntuforums.org/showthread.php?t=1288807)

---

