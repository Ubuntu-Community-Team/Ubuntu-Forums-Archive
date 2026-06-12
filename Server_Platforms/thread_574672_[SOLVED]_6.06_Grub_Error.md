---
title: "[SOLVED] 6.06 Grub Error"
date: 2007-10-13
forum: Server Platforms
---

### Post by Awayne on 2007-10-13
I'm trying to install 6.06 on a server and every time I install it, clean install, GRUB gives me an error 18. I'm not sure what causes it but I know it's what keeps me from using Ubuntu as a server OS. Is there any direct way of fixing this after install?

---

### Post by MJN on 2007-10-13
It si most likely that you've probably got an old(er) BIOS which is unable to see past the 1023rd cylinder at boot time.

The 'cure' is to create a seperate partition for /boot at the beginning of the disk (wholly within the 1023 cylinder boundary).

Do shout if you require further explanation.

Mathew

---

### Post by Awayne on 2007-10-13
Thank you for the information, I'll manually set the partitions and see if it cures it, again, thanks.

---

