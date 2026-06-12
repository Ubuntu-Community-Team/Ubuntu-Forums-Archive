---
title: "Grub broken"
date: 2017-10-15
forum: Ubuntu/Debian BASED
---

### Post by farestp on 2017-10-15
Hello, hmm, i haven't installed kubuntu, but i installed KDE Neon. And after finished the installation and restart, my laptop had show the grub command, not login console. And i try to repaired it with boot-repair, but nothing comes. I have 3 boot, there're win 10, linux mint cinnamon 18.2, and KDE-Neon. I can enter win 10 by changing the boot menu, but i cannot enter kde neon and linux mint because it stopped on grub command. There're some files in my ext4 partition, so I cann't open it.

Here's the pastebin, i hope some people can help me. I'm newbie. 
[http://paste.ubuntu.com/25746118](http://paste.ubuntu.com/25746118)

Thank you

---

### Post by howefield on 2017-10-15
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2017-10-15
Does either Neon or Ubuntu entry work from UEFI?

You have an issue with grub reinstall. Boot-Repair choose to reinstall grub for Neon install in sdb5.
error: syntax error.

Not sure what that may be.

What brand/model system?
You have the occasional system that makes the flash drive sda. 
And Ubuntu's version of grub only installs UEFI boot loader to sda, so that may be part of problem.
If your own built system, move drive to first SATA port SATA0.

---

### Post by farestp on 2017-10-16
Hmm, I can boot from usb with UEFI mode

---

### Post by farestp on 2017-10-16
Thanks guys. I solved this with boot-repair and choose advances option --> make default os linux mint cinnamon 18.2. After that i can boot to linux mint and didn't stuck at grub console. After this I re-install the KDE Neon again, and now I can boot to linux mint, kde, and win 10.

However I don't know what is the real problem

;)

---

