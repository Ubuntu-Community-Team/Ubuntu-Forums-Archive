---
title: "Can't run .exe in wine?"
date: 2011-01-03
forum: Wine
---

### Post by idavid on 2011-01-03
The file '/home/user/Desktop/Adobe Photoshop CS5 Extended/Adobe Photoshop CS5.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Does any one knows how to run it? terminal guess?

---

### Post by cheapie on 2011-01-03
Right-click the file, click Properties, go to "Permissions" tab, check "Allow executing file as program. Alternatively, you can use chmod from the terminal.

---

### Post by Vaphell on 2011-01-03
right click it, set it to executable somewhere in preferences

alternatively
```
wine /home/user/Desktop/Adobe Photoshop\ CS5 Extended/Adobe\ Photoshop\ CS5.exe
```

---

### Post by Elfy on 2011-01-03
moved to wine.

Right click - permissions - mark as executable should do the job

This is one of those questions likely to have been asked at least once,you can find some ubuntu specific search engines - some like [googlbuntu]("http://www.googlubuntu.com/") have a firefox search plugin - I use that quite often that will likely help while you find your feet.

---

### Post by idavid on 2011-01-03
> **cheapie said:**
> Right-click the file, click Properties, go to "Permissions" tab, check "Allow executing file as program. Alternatively, you can use chmod from the terminal.
tks that did it!!! feel kind of stupid asking this.. but guess thats the only way to learn!:popcorn:

---

### Post by Elfy on 2011-01-03
> **idavid said:**
> tks that did it!!! feel kind of stupid asking this.. but guess thats the only way to learn!:popcorn:

There are no stupid questions only stupid answers.

---

