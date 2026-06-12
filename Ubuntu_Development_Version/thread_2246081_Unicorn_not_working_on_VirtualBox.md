---
title: "Unicorn not working on VirtualBox"
date: 2014-09-28
forum: Ubuntu Development Version
---

### Post by chenriques on 2014-09-28
Hi.

I was trying to test Unicorn final beta on VirtualBox, but after installation and reboot the Ubuntu Greeter is not shown.
I only get this:

[IMG]http://i.imgur.com/AKe7G4B.jpg[/IMG]


Any idea?

---

### Post by Elfy on 2014-09-28
[lpbug]1371651[/lpbug]

probably

---

### Post by chenriques on 2014-09-28
> **Elfy said:**
> [lpbug]1371651[/lpbug]

probably

Thanks for the link :)

Fixed the problem with this:

1. In **/etc/default/grub** change:
 
```
[COLOR=#333333][FONT=monospace]GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
```

to

```
[COLOR=#333333][FONT=monospace]GRUB_CMDLINE_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]LINUX_DEFAULT=""[/FONT][/COLOR]
```

2. Update grub

```
sudo update-grub
```

---

