---
title: "emulate a virtual desktop"
date: 2010-05-31
forum: Wine
---

### Post by launchy on 2010-05-31
how can i enable this option to only one application e.g. warcraft 3 and disable it for the rest of the .exe i use?

---

### Post by cogadh on 2010-05-31
I believe application profiles can do that, as well as command line parameters. 

For the application profile, run winecfg and on the first tab that comes up, create a new profile for the application. Make sure that profile is selected, then go to the graphics tab to set the virtual desktop setting.

If that doesn't work, then you can just modify your command line. I hope I'm remembering this right (I don't do this that often), but the command should be formatteed something like this:
```
wine explorer /desktop=1024x768 whatever.exe
```

---

### Post by launchy on 2010-05-31
thanks cogadh! adding application to the profile did the trick:popcorn:

---

