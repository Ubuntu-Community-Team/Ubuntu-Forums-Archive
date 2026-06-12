---
title: "Can I specify the &quot;run in&quot; directory?"
date: 2010-04-30
forum: Wine
---

### Post by viktorzk on 2010-04-30
Hello,

I want to add an .exe program to my main (not wine) menu. In 'launcher properties' of the menu launcher, I have set 'command' to '/path_to_program(not in .wine)/AAA.exe'. The program opens, but reports that a file (in the same directory as the executable) is missing. The file is present, and when I doubleclick AAA.exe from nautilus, the program runs perfectly. I think that in Windows there was a 'run in' property of shortcuts, is it possible that wine tries to run the program from another directory? How can I fix this?

Another thing I tried was creating an executable file in the program directory with contents "./AAA.exe". Doubleclicking this file runs the program without problems. When I set the file as the command of the menu launcher and click the menu entry, nothing happens. However, if I change the file contents to "gedit" and click the menu entry, gedit opens. What is going on?

Thanks!
Viktor

---

### Post by cogadh on 2010-04-30
Easiest way to do it is probably to create a script to launch the app, then point the shortcut at that script:
```
#!/bin/sh
cd "$HOME/App/Directory/"
wine app.exe
```

---

