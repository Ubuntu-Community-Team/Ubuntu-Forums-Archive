---
title: "How remove errant directory"
date: 2009-09-22
forum: Security
---

### Post by onespeedbiker on 2009-09-22
Well I did something stupid and now I can't undo it. I needed to put a file in a File System directory so a program could locate it. Instead of using /tmp I used /cdrom. The files were DVD file structure files Audio_TS and Video_TS. Turns out I can't modify files in this directory and I can't delete them. I tried:
sudo rmdir -r /cdrom/VIDEO_TS 

and got rmdir: failed to remove `/cdrom/VIDEO_TS': Read-only file system

how do I do this?

---

### Post by scragar on 2009-09-22
Could you try:```
mount
```To see what's mounted and where, and if there's something mounted over those files try remounting it, see if that works:
```
sudo mount -o remount,rw **/dev/DEVICE**
```

---

### Post by yaroto98 on 2009-09-22
wouldn't a

```
sudo rm -rf /cdrom/VIDEO_TS
```

work better? It sounds like it's copied to that folder, not mounted from the dvd.

---

### Post by onespeedbiker on 2009-09-22
> **yaroto98 said:**
> wouldn't a

```
sudo rm -rf /cdrom/VIDEO_TS
```work better? It sounds like it's copied to that folder, not mounted from the dvd.
  That worked! THX

---

