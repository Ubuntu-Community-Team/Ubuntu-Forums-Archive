---
title: "Restricting wine from removable drives"
date: 2009-08-10
forum: Wine
---

### Post by rahulabc on 2009-08-10
I am using Ubuntu Hardy 64 bit. I have installed wine because I need IEs4Linux but now I am worried about viruses. Every time I attach a Flash Drive, I have to restart and open Windows to check viruses. Is there a way to stop wine to work with removable drives and CDs?

Any help would be greatly appreciated..

---

### Post by Vegan on 2009-08-10
Unfortunately there is no way to stop Linux from mounting USB sticks as its intentionally set to recognize them.

If you need Windows that badly, then go buy a Windows machine.

---

### Post by rahulabc on 2009-08-10
I dont like Windows n I dont want to stop mounting of removable drives. I juz want to stop giving access to wine to them..

---

### Post by NightMKoder on 2009-08-10
You can unmap the Z: drive in winecfg, but I'm pretty sure wine uses HAL for recognizing storage devices.

Don't worry about viruses too much though - most of them don't work too well on wine and plus - they can't start on startup (wine doesn't support that).

---

### Post by rahulabc on 2009-08-10
ok..
a big thnx for ur help.. :)

---

