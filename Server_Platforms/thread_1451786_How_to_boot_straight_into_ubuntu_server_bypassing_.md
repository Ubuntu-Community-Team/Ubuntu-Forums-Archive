---
title: "How to boot straight into ubuntu server bypassing grub"
date: 2010-04-11
forum: Server Platforms
---

### Post by danushk on 2010-04-11
Hi guys,

I was running a ubuntu server on another PC which has no keyboard. only power and lan cable is connected and i was remotely admining it from my desktop PC. 

When i turned that Server PC on earlier , it goes straight into user login screen of ubuntu server. But right now i see the grub menu list which is expecting the keyboard Enter input.

how do i remove that so later on i don't need to plug the keyboard and hit enter to goto server login ?

---

### Post by dominiquec on 2010-04-11
GRUB is part of the boot process, so you can't really bypass it.  But you can reduce the time it spends waiting for input. There should be a timeout option in your menu.lst file (assuming you're using GRUB and not GRUB2.)  You can set this to 0 or a low number.

Please see [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto).

If you're using GRUB2, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Skidbladnir on 2010-04-11
He is; GRUB2 autoboots if there isn't another OS.

---

### Post by trig on 2010-04-11
I didnt know you could bypass the GRUB, I thought it was a inportant part of the process?  You see when i deleted part of the grub, nothing worked and i had to reinstall.

---

### Post by fang0654 on 2010-04-11
Grub is vital and necessary to boot your system.  Grub is what actually starts booting the operating system.  Even if it is giving you multiple options, it usually defaults after a few seconds to the first option, so headless, you won't need to worry about it.

---

