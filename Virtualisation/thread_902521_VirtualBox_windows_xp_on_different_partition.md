---
title: "VirtualBox: windows xp on different partition"
date: 2008-08-27
forum: Virtualisation
---

### Post by Arrowx7 on 2008-08-27
Hello,
I installed windows xp on a separate hard drive and made a dualboot system.
Now I would like to load windows without having to reboot my ubuntu machine.

I was thinking I can do this with virtual box, so I set up a real hard disk image (used /dev/sda1) and launched it.  Right after it gave the "Virtual Box" spash screen, it gives me a black cursor at the top-left of the screen...that's it.

I can still load windows if I physically reboot to it.

Any idea how  I can fixed this problem with virtual box, or what the cursor on top-left means?  Is there any other software that would be more suited for what I'm trying to do?

Thanks!

---

### Post by WRDN on 2008-08-27
Due to the fact Virtual machines use Virtual hard drive images (in the case of Virtual Box, .vdi files are created), you cannot load a 'real' installation into a Virtual Machine (i.e. the OS files on a real partition). If you wish to boot XP in a Virtual Machine, you will have to install XP in it.

---

### Post by b0b138 on 2008-08-27
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

