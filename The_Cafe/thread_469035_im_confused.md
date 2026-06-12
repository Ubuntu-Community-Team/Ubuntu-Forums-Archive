---
title: "im confused"
date: 2007-06-09
forum: The Cafe
---

### Post by brandonxlx on 2007-06-09
ok i installed ubuntu fiesty on my desktop again last night. all was great but then when i restarted after doing updates my computer went haywire. it went in to continuous cycles of rebooting. i dont know why...... can anyone tell me why this may have happened?

---

### Post by Nonno Bassotto on 2007-06-09
You should add more details and post in a suitable (help) section.

---

### Post by brandonxlx on 2007-06-09
ok like what details? and the reason i posted it here was because i wasnt sure where to put it.

---

### Post by starcraft.man on 2007-06-09
> **brandonxlx said:**
> ok like what details? and the reason i posted it here was because i wasnt sure where to put it.

Post[ here please.]("http://ubuntuforums.org/forumdisplay.php?f=73")

As for what details... tell us what updates you were applying and anything you did before and after they were applied that modified the system. I'm not exactly sure what could cause your computer to just senselessly reboot...

---

### Post by Outrunner on 2007-06-09
At bootup, there should be a GRUB menu(if not it will ask you to press ESC if you want to view it) for a few seconds. Are you booting into the -16 kernel(is it highlighted)? If so, use the down arrow button to select the -15 kernel and boot it(press Enter)

By the way, I did a lot of guessing here bsed on the fact that you mentioned updates. If this is not it, you'll need to provide more details as stated above.

---

### Post by YourSurrogateGod on 2007-06-09
Silly question, how can one edit that list of bootable operating systems that GRUB displays?

---

### Post by brandonxlx on 2007-06-09
... maybe i did something the wrong way
should i just reinstall it? and then report what happens?

---

### Post by Outrunner on 2007-06-09
> **YourSurrogateGod said:**
> Silly question, how can one edit that list of bootable operating systems that GRUB displays?

In /boot/grub/menu.lst. Be careful there though, I don't think you want to ruin that file.

---

### Post by YourSurrogateGod on 2007-06-09
> **Outrunner said:**
> In /boot/grub/menu.lst. Be careful there though, I don't think you want to ruin that file.

Thank you.

I usually make backups of previous files though.

---

### Post by brandonxlx on 2007-06-09
Hello? should i just reinstall it and post what happens?

---

### Post by Outrunner on 2007-06-09
Did the above instructions not work for you?

---

