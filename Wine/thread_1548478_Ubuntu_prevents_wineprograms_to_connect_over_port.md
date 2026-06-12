---
title: "Ubuntu prevents wineprograms to connect over port?"
date: 2010-08-08
forum: Wine
---

### Post by JavaRat on 2010-08-08
Hello everyone,

I am using Ubuntu 9.10 at the moment and recently installed a program called "FujiDirekt" in wine which can be found at:  [http://http://www.fujidirekt.se/fotobok/FujiDirektSE.exe]("http://http//www.fujidirekt.se/fotobok/FujiDirektSE.exe")

The program will install and start perfectly but it immediately tries to autoupdate which fail.
(The program works on my friends windows XP).
I am suspecting that the program is trying to connect to a remote server over a port which Ubuntu refuses. Is there some way which I can confirm this? 
And if so can I find the port which it needs and then open it?

Thank you for your time and assistance!
/JavaRat

---

### Post by asdfoo on 2010-08-09
I doubt your hypothesis.

Instead: open a terminal, type `wine --version`, if it does not say atleast wine-1.2 or wine-1.3.0 you need to get a newer version and retest.

---

### Post by JavaRat on 2010-08-09
Thank you for your reply asdfoo.

With wine version 1.2 or 1.3 (also tried using Ubuntu 10.04) 
I get the following output starting the application from a terminal with this command:

```
pc1@ubuntu:~$ wine .wine/drive_c/Program\ Files/Fujidirekt\ SE\ Fotoservice/Fujidirekt\ SE\ Fotoservice.exe
err:ole:CoUninitialize Mismatched CoUninitialize
pc1@ubuntu:~$ fixme:advapi:LookupAccountNameW L"" L"Everyone" 0x33fc20 0x33fc8c
0x1326c8 0x33fc88 0x33fc84 - stub
error : unterminated entity reference Posters
error : unterminated entity reference Posters
pc1@ubuntu:~$
```...any ideas to what the problem might be?

---

