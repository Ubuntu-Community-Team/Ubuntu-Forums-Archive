---
title: "WoW using wine package &amp; nvidia glx"
date: 2006-04-22
forum: Wine
---

### Post by keeran on 2006-04-22
Hi all, apologies in advance if this is posted in the wrong place, but I'm having difficulty finding any information on this problem.

I have installed dapper x86 and nvidia-glx for xorg, wine 0.9.12 from the official repository.

I have tried various patched installations etc as per the usual guides, all end up with the following error:

```

khawoldar@ether:~$ wine .wine/drive_c/games/World\ of\ Warcraft/WoW.exe 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  144 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24a
  Serial number of failed request:  355
  Current serial number in output stream:  355

```

My google travels have indicated this could be something to do with xinerama, but I'm not getting very far using the opcodes as keywords etc, so I thought I would ask you guys if anything is obvious to you.

I'm running a dual head system btw, hence the xinerama thought.. any help would be greatly appreciated - this game is the only thing I have left to migrate to this wonderful operating system :)

TIA - Kee

---

### Post by little cazy on 2007-09-04
[http://http://ubuntuforums.org/showthread.php?t=286646&highlight=wine+badwindow]("http://http://ubuntuforums.org/showthread.php?t=286646&highlight=wine+badwindow")

---

### Post by cogadh on 2007-09-04
Dude, your link has an extra "http" in it, it doesn't work.

keeran, that version of Wine is way out of date, update to the latest version 0.9.43:
[http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)

---

