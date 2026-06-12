---
title: "open programs with wine in rox"
date: 2009-06-27
forum: Wine
---

### Post by user sam on 2009-06-27
I use rox as my file manager most of the time, but I cannot seem to associate wine with windows programs in it. I right click the windows .exe file and select set run action. Then I type "wine" (w/o quotes) before "$@" (w/ quotes). It doesn't work. I can use other programs, like pcmanfm, progman, and the terminal, to open my program, but since rox is also my desktop it is much easier to use.
I can open windows programs from the terminal, but only if I cd all the way to the directory that they are in. 
for example:
cd .wine
cd drive_c
cd program_files
cd example
wine example.exe

And I have to do it exactly like that. I can't just say 
wine .wine/drive_c/program_files/example/example.exe
The directory had a ! that was confusing the terminal, but it didn't work in rox even after I got rid of the !. Does anyone know what the problem is?

---

### Post by user sam on 2009-06-28
I give up. I'm using lxde. only a little bit slower.

---

