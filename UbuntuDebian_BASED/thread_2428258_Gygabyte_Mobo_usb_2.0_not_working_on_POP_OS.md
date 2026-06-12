---
title: "Gygabyte Mobo usb 2.0 not working on POP OS"
date: 2019-10-01
forum: Ubuntu/Debian BASED
---

### Post by playersome on 2019-10-01
I have tried the method below, and so far has not worked. anyone have suggestions?


"[COLOR=#000000]Here is my updated fix[/COLOR]

[COLOR=#000000]First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi[/COLOR]

[COLOR=#000000]plug your usb mouse, keyboard and thumbdrive in usb 2 ports.[/COLOR]

[COLOR=#000000]save and exit the uefi[/COLOR]

[COLOR=#000000]Then In Ubuntu:[/COLOR]

[COLOR=#000000]press Ctrl+Alt+T to open up a terminal[/COLOR]

[COLOR=#000000]run the following command: sudo gedit /etc/default/grub[/COLOR]

[COLOR=#000000]Only edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"[/COLOR]

[COLOR=#000000]save changes to grub and exit gedit and the terminal[/COLOR]

[COLOR=#000000]Open up a new terminal with ctrl+alt+t[/COLOR]

[COLOR=#000000]run the following command: sudo update-grub[/COLOR]

[COLOR=#000000]then exit the terminal using this command: exit[/COLOR]

[COLOR=#000000]Restart your computer press delete to get back into the uefi[/COLOR]

[COLOR=#000000]Disable iommu in bios, load optimized defaults and restart.[/COLOR]

[COLOR=#000000]usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios may also help improve your boot times.[/COLOR]

[COLOR=#000000]If the above post helps anyone I am happy.  "

*UPDATE i found the solution in this video [/COLOR][https://www.youtube.com/watch?v=_ky20Ywo3Eo](https://www.youtube.com/watch?v=_ky20Ywo3Eo)

---

### Post by playersome on 2019-10-01
How do i set this as solved in the forum? Is that only a mod thing?

---

### Post by wildmanne39 on 2019-10-01
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

To mark your thread solved use thread tools at the top of your first post.

---

