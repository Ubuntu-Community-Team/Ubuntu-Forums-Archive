---
title: "WINE with Play on Linux"
date: 2011-01-30
forum: Wine
---

### Post by pi3.1415926535... on 2011-01-30
Hello,
I have installed WINE 1.2 and 1.3 (removed 1.2) and Play on Linux on Ubuntu 10.10, though both have the same error, which is that when I try to open most .exe files after a few minutes of nothing happening, a message pops up saying "There is no Windows program configured to run this type of file". In addition, when I try to open the WINE entry on the menu, which did not appear by default after installing wine, it says the the file is not marked as executable. The command running is "cautious-launcher %f wine start /unix".

Thank you

---

### Post by davidmohammed on 2011-01-30
open a terminal session

cd <where ever your exe is>

e.g.

cd Downloads

wine <exe name>

e.g.

wine mytestexe.exe

any error messages?

---

### Post by pi3.1415926535... on 2011-01-30
Hello,
When I try that, it responds;
"err:process:__wine_kernel_init boot event wait timed out
wine: Bad EXE format for Z:*filelocation*"
(The actual error does not include a smiley face, it includes : p without the space instead, though that is understood as the smiley face)

Thank you

---

### Post by davidmohammed on 2011-01-31
try cleaning up your wine installation and try reinstalling

open your home folder - choose view - show hidden files.

Look for ".wine" - delete or rename it.

then open a terminal

type winecfg to initialise wine

then try

wine <your exe name>

---

### Post by pi3.1415926535... on 2011-01-31
Thank you, though when I tried that, the result was:
"wine: Bad EXE format for Z:\file\location.exe"
(Does wine have any thing to do with the direction of the slashes, which, for locations are normally /, rather than \?)

---

### Post by pi3.1415926535... on 2011-02-06
Any ideas?

Thank you

---

### Post by davidmohammed on 2011-02-08
from what I've read "Bad EXE format" is a general error indicating that it doesnt think your .exe is actually an executable - it is probably corrupt.

---

