---
title: "VLC Player"
date: 2012-05-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-30
Is anyone else having trouble with vlc player ?? I have no GUI just a white window where the gui should be, it runs videos ok but the only way to close it is by the icon at the top of the screen, 
Run from terminal; output;

X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0

add infinitum

Regards Miykel

---

### Post by mc4man on 2012-05-30
I do see some potential issues possible with vlc & some other qt apps, posted a thread on recently
Don't see here as  you've described -  so first make sure vlc is using the qt interface
from cli
```
vlc -Iqt4
```

If still no good then you could try this - if vlc works better then it's related to bug I see , if not then you've some other issue

Start vlc from cli with
```
LIBOVERLAY_SCROLLBAR=0 vlc -Iqt4
```

If still no good then maybe try deleting ~/.config/vlc

---

### Post by Miykel on 2012-05-31
Thanks for the reply mc4man; I tried the fixes but no good so I done a fresh install of the OS then vlc, seemed to run ok until I opened preferences, then I went crazy again, the player will only onpen in full screen now and the preference window half opens, white page with bits and pieces of the options, I run the 

LIBOVERLAY_SCROLLBAR=0 vlc -Iqt4

command and that fixed it but only if I run that command every time, if I just click on the icon I get the full screen and if I open anything else it goes crazy, hard to explain what it does, the window that opens, opens half way down the screen then jumps up the width of the top border and keeps going until I close the player.

Deleting the config/vlc helped once then the next time back to fullscreen
Regards Miykel

---

### Post by mc4man on 2012-05-31
> **Miykel said:**
> Thanks for the reply mc4man; I tried the fixes but no good so I done a fresh install of the OS then vlc, seemed to run ok until I opened preferences, then I went crazy again, the player will only onpen in full screen now and the preference window half opens, white page with bits and pieces of the options, I run the 

LIBOVERLAY_SCROLLBAR=0 vlc -Iqt4


The issue is described in this thread. inc.'s some workarounds
[http://ubuntuforums.org/showthread.php?t=1988663](http://ubuntuforums.org/showthread.php?t=1988663)
There is a link there to old bug when this occurred a yr. ago

Did start a new one, maybe new qt4 libs when they show will resolve, maybe not, if not the hope is it won't drag on like last time

new report - 
[https://bugs.launchpad.net/bugs/1005677](https://bugs.launchpad.net/bugs/1005677)

---

