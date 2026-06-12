---
title: "What does it means?"
date: 2011-03-06
forum: Wine
---

### Post by iulian.baciu on 2011-03-06
I recently installed FIFA Manager 06 using Wine.
The problem is whenever I try to play it shows me this:

"FIFA Manager 06 requires at least 525 MB of free swap file space.
Please free the required space and re-run the game. "

Well, I have a swap disk partition that is about 4.5 GB, where the computer use around 60 MB. If it concerns the memory, there is a 1 GB ram, around 520 MB being used.
So, why I can't play the game?

---

### Post by mips on 2011-03-06
Forget about your linux swap partition. This problem is related to the Windows Swap File.

Windows uses a swap file for purposes similar to linux using a swap partition. You need to modify the windows swap file size.

[http://ubuntuforums.org/showthread.php?t=1511599](http://ubuntuforums.org/showthread.php?t=1511599)
Also have a look at [http://www.winehq.org/help/](http://www.winehq.org/help/)
[http://www.winehq.org/pipermail/wine-users/2007-January/024245.html](http://www.winehq.org/pipermail/wine-users/2007-January/024245.html)

---

### Post by JRV on 2011-03-06
Wine does not see the Linux swap space, your program is looking for the Windows swap file.  You will need to re-allocate memory for Wine.

I hope this points you in the right direction.
I am not familiar enough with Wine to be of further assistance.

---

### Post by iulian.baciu on 2011-03-06
ok. Thanks a lot for help. 
I wonder if there is an easier way to modify swap file size?

---

### Post by mips on 2011-03-08
> **iulian.baciu said:**
> ok. Thanks a lot for help. 
I wonder if there is an easier way to modify swap file size?

I have no idea but I reckon the people over at the WINE forums would know and you would probably get an answer quicker than here seeing they are dedicated to WINE.

---

