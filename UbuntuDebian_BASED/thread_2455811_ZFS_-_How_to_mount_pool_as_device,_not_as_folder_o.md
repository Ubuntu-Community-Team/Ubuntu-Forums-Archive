---
title: "ZFS - How to mount pool as device, not as folder off root"
date: 2020-12-28
forum: Ubuntu/Debian BASED
---

### Post by robbrown99 on 2020-12-28
Hello, I am migrating to KDE Neon and bringing a ZFS pool with me. On my Mac I had OpenZFS installed.

I installed the latest ZFS [https://zfsonlinux.org/](https://zfsonlinux.org/)  and imported my pool. However rather than importing and have it listed  as a separate device (as it does on Mac), it imported as a folder off  root on my system disk.

Is there a method of changing the mount  point when importing the pool (or doing it after the fact) to make it  show up as a device adjacent to my system drive? I can't find anything  about this in the import documentation. 

Thank you

---

### Post by howefield on 2020-12-28
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by CharlesA on 2020-12-28
Hi, ZFS will always be mounted as a folder, rather than showing up as a device in the GUI.

You can work around it by bookmarking the folder the pool is mounted under and you are able to change the mountpoint via the following command:
```
sudo zfs set mountpoint=/media/$USER/folder poolname
```

---

### Post by robbrown99 on 2020-12-28
Thanks for the info Charles

I tried relocating as you described, but for some reason I don't see the folder now...

I ran this (no errors)
[FONT=monospace][COLOR=#000000]sudo zfs set mountpoint=/media/rbrown/BigDiskZFS BigDis[/COLOR]kZFS

Then I went to the folder and looked for it:
[FONT=monospace][COLOR=#18b218]**rbrown@rob-macpro**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818b2]**/media/rbrown**[/COLOR][COLOR=#000000]$ ls [/COLOR]
[COLOR=#1818b2]**'Macintosh SSD'**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#1818b2]**'Recovery HD'**[/COLOR]
[COLOR=#000000] [/COLOR]

But I only see two other drives in there ^

What am I doing wrong here?

[/FONT]

[/FONT]

---

### Post by robbrown99 on 2020-12-28
OK strange. After exporting, then reimporting, the zpool shows under the media/$USER folder. I guess I fixed it. 

[FONT=monospace][COLOR=#18b218]**rbrown@rob-macpro**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818b2]**/media/rbrown**[/COLOR][COLOR=#000000]$ ls[/COLOR][/FONT]
[FONT=monospace][COLOR=#1818b2]**BigDiskZFS**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#1818b2]**'Macintosh SSD'**[/COLOR][COLOR=#000000]  [/COLOR][COLOR=#1818b2]**'Recovery HD'**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#18b218]**rbrown@rob-macpro**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818b2]**/media/rbrown**[/COLOR][COLOR=#000000]$ [/COLOR]

I also added it as a location in the file manager as a shortcut on the side bar.

Thanks for your help.


[/FONT]

---

