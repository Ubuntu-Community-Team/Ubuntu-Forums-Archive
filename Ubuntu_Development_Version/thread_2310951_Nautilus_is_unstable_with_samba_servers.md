---
title: "Nautilus is unstable with samba servers"
date: 2016-01-23
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-01-23
Hello, I'm using a Raspberry Pi with samba to share directories. It works fine with Windows and also with Ubuntu but often, on Xenial, Nautilus freezes. I need to open a terminal, launch a "killall nautilus" command and it starts to work again. The dash works fine so I open a terminal and launch that command. Few times it freezes the whole DE and I need to reboot via CTRL+ALT+F1 shell.



 
 
 I just wanted to point out this. It's not a big bug, but it's annoying sometimes. has someone the same problem?

---

### Post by dino99 on 2016-01-23
i've not met your issue, but my configs are way differents than yours too ;)
maybe its happening because of path typo or rights; glance at your logs to find more. :p

---

### Post by enricobe on 2016-01-24
I don't know because it usually works fine. I can copy GBs of files with no problems from and to the Raspberry Pi. It seems that nautilus freezes when looking for shared directories or PCs. If it doesn't freeze when it looks for network devices/directories it works fine until the next reboot.

---

