---
title: "Installation and use Jeskola Buzz through WINE .. didn't work"
date: 2008-08-23
forum: Ubuntu Studio
---

### Post by Ash44455666 on 2008-08-23
Hello everyone.  First of all, sorry if I didn't post my thread in the correct subforum, but I tried to choose the subform carefully.

So, I'm trying to install [Jeskola Buzz]("http://buzzmachines.com/"), a Windows program, via WINE.  I've heard of other successful cases (there's an [example at YouTube]("http://www.youtube.com/watch?v=Vuqh9mOZQ2I") of successful installation and use of Buzz in Ubuntu), but it didn't go quite as perfectly as planned.

By the way, I haven't made any particularly "major" changes to my system; in fact, I only installed Ubuntu this morning, lol.  (Shortly after, I installed WINE)

The installation of Jeskola Buzz seemed flawless, however, when I attempted to run the program, nothing happened.  I tried running it from the Terminal via the command "wine Buzz.exe", but it gave me the following error(s):

```
caleb@caleb-laptop:~/.wine/drive_c/Program Files/Jeskola Buzz$ wine buzz.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Jeskola Buzz\\auxbus.dll") not found
err:module:import_dll Library auxbus.dll (which is needed by L"C:\\Program Files\\Jeskola Buzz\\buzz.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Jeskola Buzz\\buzz.exe" failed, status c0000135
```

Any suggestions?

---

### Post by Ash44455666 on 2008-08-23
Aha, I fixed the installation/running problem.
Curious, I had gone to the WINE website to see current progress, version(s), etc.  and it turned out I had version 1.0, the "stable" release.  Since it wasn't working as I wanted, the very recently released development release 1.1.3 looked promising.  Following the instructions, I installed the new WINE, and tried running Jeskola Buzz.  It worked without complaint!  The only problems that I'm still having involve missing machines (.DLLs) that I need to be able to open an old song of mine, but hopefully I can fix that with some copying, downloading, or however I can do it.  Thanks for reading my thread, I hope this ends up helping someone!

---

