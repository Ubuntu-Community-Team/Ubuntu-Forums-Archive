---
title: "How to install IE6 into pre-made prefix"
date: 2010-03-25
forum: Wine
---

### Post by J V on 2010-03-25
I need to install IE6 into a prefix I already created... Anyone know how?

---

### Post by beastrace91 on 2010-03-25
```
WINEPREFIX=$/path/to/prefix wine IEset.exe
```

Obviously replace the /path/to/prefix with the path to the prefix you would like to use and then replace IEset.exe with the path to your IE6 setup.exe

Also [winetricks]("http://wiki.winehq.org/winetricks") will auto install IE6 and everything it needs to run FYI.

Lastly - more info on [Wineprefixes]("http://wiki.jswindle.com/index.php/Wine_Prefixes")

~Jeff

---

