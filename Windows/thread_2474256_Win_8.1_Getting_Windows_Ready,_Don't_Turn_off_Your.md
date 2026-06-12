---
title: "Win 8.1: Getting Windows Ready, Don't Turn off Your Computer"
date: 2022-04-25
forum: Windows
---

### Post by maketopsite on 2022-04-25
It has happened after Win. update.

Minimal CPU load (because of silent CPU fan), minimal hard disk activity after more than 3 hours of waiting. Animated icon was still rotating. Then I've powered off laptop, removed power cable, all connected devices - mouse, usb stick, headphone. I've pressed power off button for 30 seconds. Then I've started laptop and tried to boot Windows but it did not help. Any way to fix it please ?

There is another problem when mounting Win. partition from linux: 

```
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
```

---

### Post by ajgreeny on 2022-04-25
I think you will do better asking the same question in a Windows forum as many of us here are now unable to give Windows users much help; this is a **Ubuntu Linux** Forum, not a Windows forum.

For your sake, I hope I am wrong, but good luck with this query anyway.

---

### Post by yancek on 2022-04-25
The error you get from Linux when trying to access window generally means windows is hibernated. Some windows updates will turn it on without telling/asking you if you want it done.  You can't run chkdsk from Linux.

If you can boot windows to a command prompt, try running chdsk.  If that dooesn't work, I'd also suggest going to the microsoft support site or a windows forum.

---

### Post by maketopsite on 2022-05-07
Thank to all.

Solved. Details here: [https://forums.techguy.org/threads/win-8-1-getting-windows-ready-dont-turn-off-your-computer.1277205/](https://forums.techguy.org/threads/win-8-1-getting-windows-ready-dont-turn-off-your-computer.1277205/)

---

