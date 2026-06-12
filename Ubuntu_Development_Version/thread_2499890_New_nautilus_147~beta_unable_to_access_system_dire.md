---
title: "New nautilus 1:47~beta unable to access system directories"
date: 2024-08-14
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-08-14
'Other Locations' disappeared in left panel so I can not access 'Ubuntu' and system directories.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979)

---

### Post by deadflowr on 2024-08-17
i see that even though they've removed Other Locations, they have also moved all external media back to the side panel.
That was my only real concern, for second I thought they'd want users to use gnome-disks to quickly mount stuff, which I don't think would work well.
(I foresaw a lot of users wanting to know where something was and realizing they'd done some finagling in gnome-disks and broke a partition, or two.)
 
Seems easy enough to bookmark / for system file accessibility.

---

### Post by corradoventu on 2024-08-17
The bug is fixed, update should arrive soon. Now also baobab lists all partitions and allows mounting.

---

### Post by Claus7 on 2024-08-17
Hello,

now Desktop can take its place on the left hand hide as a new Bookmark with the rest of the locations. Installing today's iso I was not able to see on the left "Other locations" and I had to create a bookmark for / by editing /home/user and removing the home/user string. A more practical way would be nicer I guess unless I missed something, yet still is under development.

Regards!

---

### Post by corradoventu on 2024-08-18
The bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979) is NOT fixed but closed as 'won't fix' so you must 
You can access the root of your filesystem by simple typing / and Enter or Ctrl+l and navigating to their directory directly

---

### Post by MyMurry on 2024-08-18
And then you can add a bookmark for it.

---

### Post by Morbius1 on 2024-08-18
Did you all catch the reason for it's removal:
> António Fernandes
@antoniof · 2 days ago
Maintainer

The meaning of folders with cryptic names (etc, usr, and so on) is not easy to explain to a beginner.


I think I am now too old for Gnome. 

Do any of you folks know if Thunar does this as well or is it strictly confined to Nautilus.

---

### Post by #&amp;thj^% on 2024-08-18
> **Morbius1 said:**
> Did you all catch the reason for it's removal:


I think I am now too old for Gnome. 

Do any of you folks know if Thunar does this as well or is it strictly confined to Nautilus.

Not here, Full XFCE4.
```
thunar --version
thunar 4.19.3 (Xfce 4.18)

Copyright (c) 2004-2022
	The Thunar development team. All rights reserved.

Written by Benedikt Meurer <benny@xfce.org>.

Please report bugs to <https://gitlab.xfce.org/xfce/thunar>.

```

---

