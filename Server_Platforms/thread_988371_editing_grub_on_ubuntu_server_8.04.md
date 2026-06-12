---
title: "editing grub on ubuntu server 8.04"
date: 2008-11-20
forum: Server Platforms
---

### Post by drtanz on 2008-11-20
hi i would like to edit my grub so that it will load windows by default instead of my ubuntu server. how can i do this? thanks

---

### Post by MJN on 2008-11-20
If you post your /boot/grub/menu.lst file then we can tell you what parameter to change (and what to).

Alternatively, I could just tell you that it's the 'default' directive that needs to be changed however you need to be aware that the numbering starts at zero and that section dividers count as a line towards numbering each menu statement.

If you want to try it, reboot your machine and hit Escape at the Grub prompt - find the XP entry and note its position - remember start counting at zero and include dividers as an entry - then edit the 'default' directive accordingly.

For example, the following would require **default 3** to load XP.

(0) Ubuntu
(1) Ubuntu (Recovery)
(2) --- Other OS's ---
(3) XP

Incidentally, whilst you're at it you might want to change the 'timeout' setting as required, along with commenting out 'hiddenmenu' if you want the menu to always appear (without pressing Escape).

Mathew

---

### Post by drtanz on 2008-11-20
tried to use gedit to get to the menu.lst file but apparently gedit is not installed and i havent yet managed to get internet access on the server yet. is there another way to get into that file and edit it? thanks

---

### Post by jamb on 2008-11-20
> **drtanz said:**
> tried to use gedit to get to the menu.lst file but apparently gedit is not installed and i havent yet managed to get internet access on the server yet. is there another way to get into that file and edit it? thanks

In a terminal type
cd /boot/grub
sudo nano menu.lst

---

