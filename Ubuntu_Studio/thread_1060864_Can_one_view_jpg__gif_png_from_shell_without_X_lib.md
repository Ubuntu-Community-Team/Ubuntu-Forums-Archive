---
title: "Can one view jpg / gif/ png from shell without X libs"
date: 2009-02-05
forum: Ubuntu Studio
---

### Post by bonevg on 2009-02-05
Can I view my photo collection without having X installed
To put it into other words.. Is there a tool to load the image directly from my shell. Let`s say I have case where only server packs are installed without X system.

e.g. is there a tool something like:
$imageviewer mypic.jpg .. where imageviewer is the imaginary tool I`m looking for :)

---

### Post by xopher_mc on 2009-02-05
How are you accessing the computer. You could use Places>connect to server to mount the files to a machine with a X and view them with the appropriate program.

---

### Post by bonevg on 2009-02-05
> **xopher_mc said:**
> How are you accessing the computer. You could use Places>connect to server to mount the files to a machine with a X and view them with the appropriate program.

Well that is workround.. but Im more interested in a direct approach :)

EDIT:
Ok to put some more light. Long time ago when there was mostly DOS, no mice and let`s say black and white monitors - there were tools to view graphic files from the old dos propmpt.
I would be surpised if there isn`t such tool in any *nix system, especialy Ubuntu!

---

### Post by unutbu on 2009-02-05
There is an image viewer package (and program) for frame buffer devices called fbi. To view an image, simply type
```

fbi *.jpg
```
from the text console.

For much more information on using Linux without X, see [http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

---

### Post by bonevg on 2009-02-05
> **unutbu said:**
> There is an image viewer package (and program) for frame buffer devices called fbi. To view an image, simply type
```

fbi *.jpg
```
from the text console.

For much more information on using Linux without X, see [http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

Heya, thanks for this info. I`ll go for a try.
I have also found something on the forum which satisfied my curiosity/ thx
[http://ubuntuforums.org/showthread.php?t=834607](http://ubuntuforums.org/showthread.php?t=834607)

---

