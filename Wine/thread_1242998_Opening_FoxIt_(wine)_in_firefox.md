---
title: "Opening FoxIt (wine) in firefox"
date: 2009-08-17
forum: Wine
---

### Post by ssri on 2009-08-17
Hi,

I followed this guide ([http://ubuntuforums.org/showthread.php?t=847180](http://ubuntuforums.org/showthread.php?t=847180)), but foxit neither opens the pdf in /tmp nor starts up.

I tested whatever script I made (i.e. $sh /usr/bin/foxit) to see if the wine starts up...

Foxit (wine) starts up with either

```
#!/bin/bash

env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\Foxit Software\Foxit Reader\Foxit Reader.exe"
```

or

```
#!/bin/bash

wine start /ProgIDOpen FoxitReader.Document %f
```

The second code being the command that opens up a pdf in foxit (wine) from a file browser.

However, neither command works when trying to open a pdf from firefox's dialog menu using foxit (wine).

---

### Post by jethro10 on 2009-08-20
I can't help with your problem, but do you know Foxit reader is now available directly for linux?

J

---

