---
title: "Burning a Vista Recovery partition?"
date: 2008-07-01
forum: Windows
---

### Post by TrikeKid on 2008-07-01
I ordered up a laptop recently that comes with Vista installed, not my cup o' tea so it will get Ubuntu installed pretty much upon arrival. I would like to know if I can burn the restore partition to a disk so that I could reload vista in the event I wanted to sell the laptop to someone that didn't want Linux. Is it doable? Will I be able to fully restore Vista onto a drive that's been wiped clean?

---

### Post by LaRoza on 2008-07-01
There are three things you can do:

[list]
[*] Make back up disks with a possible inbuilt program (many OEM's allow that)
[*] Contact manufactorer for complete restore disks
[*] Clone partition with a tool like Clonezilla.
[/list]

I recommend them in that order.

---

### Post by pelle.k on 2008-07-01
I have mandriva installed to an external HD, but ubuntu or arch would suffice as well. In fact, almost any liveCD would do the trick.
I used ntfsclone from "ntfsprogs". See how easy it is to backup (note that windows is what i use as a label);
```
ntfsclone -s -o - /dev/disk/by-label/windows | gzip -c > windows.ntfs.gz
```
And to restore;
```
gunzip -c windows.ntfs.gz | ntfsclone -r -O /dev/disk/by-label/windows -
```
You may use /dev/sdX as well.
I'm assuming the recovery partition is NTFS here. Maybe it's not?

If you're lazy, you can also save the MBR with "dd", and the partition table layout with "sfdisk". There's lots of guides on the net.

---

### Post by TrikeKid on 2008-07-01
Thanks guys, I didn't come up with much googling.

---

