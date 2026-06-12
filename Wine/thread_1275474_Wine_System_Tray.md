---
title: "Wine System Tray"
date: 2009-09-25
forum: Wine
---

### Post by RealG187 on 2009-09-25
I have a Windows program that creates a tray icon and I set Ubuntu up to start it with wine automatically.

The problem is I think the program loads before my Gnome system tray does so I have an extra windows called "Wine System Tray"

Is there a way I can make it so it goes to my Ubuntu/Gnome system tray?

---

### Post by beastrace91 on 2009-09-26
It might not be the most elegant method but if you create a small script to run something along the lines of ```
sleep 5
wine myprogram.exe
```

And then run the script at start up instead of directly running the Wined program it will give a 5 count before loading your program, hopefully enough time for your Gnome tray to get loaded - and if not just increase the sleep time by a couple seconds.

~Jeff

---

### Post by RealG187 on 2009-10-01
How exactly do I do that?

Do I enter it in a text file and add the path to the text file? And mark the file as executable?

Also it appears wine isn't the only program that has this issue (see attachment)

---

