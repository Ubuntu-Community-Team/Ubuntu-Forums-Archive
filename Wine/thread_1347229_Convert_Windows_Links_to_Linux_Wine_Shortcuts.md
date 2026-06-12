---
title: "Convert Windows Links to Linux Wine Shortcuts"
date: 2009-12-05
forum: Wine
---

### Post by Intel91 on 2009-12-05
I would like to know if there is currently any method or software for converting a microsoft windows shortcut into a linux launcher referencing the same .exe? Or maybe a way for wine to be declared to launch and interpret windows shortcuts. I know how to do it for one, I need to mass convert. If it doesn't exist I will go ahead and write it, but if it does then why bother.

Thanks,
Intel

---

### Post by david_kt on 2009-12-06
Open terminal and try below:

```
find $HOME/.local/share/applications/wine -type f -name "*.desktop" -exec cp -f {} $HOME/Desktop \;
```

DK

---

### Post by Intel91 on 2009-12-06
Sorry, I probably should have specified .lnk shortcuts to linux launchers. Wine can handle .desktops (I am assuming wine converts .lnk to .desktop somehow). Which is the function I am wanting to call, I want a .lnk to be converted into a interpretable shortcut/launcher/.desktop (any) for linux.

Thanks,
Intel

---

### Post by tg3793 on 2010-12-14
[This script]("http://ubuntuforums.org/showthread.php?t=1645064") is a good start on what you are trying to do. Just trying to get the script tweaked now.

---

