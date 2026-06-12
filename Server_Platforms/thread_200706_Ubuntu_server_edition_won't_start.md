---
title: "Ubuntu server edition won't start"
date: 2006-06-20
forum: Server Platforms
---

### Post by dixon on 2006-06-20
I've tried to install the ubuntu server edition on ma PC Chips 789 CG mainboard(with integrated CPU) and It won't start. Whole installation finished succesfull, but when it tries to boot for the first time It keeps rebooting.

It looks like this :)

initrd .......
savedefault
boot

And then reboot.....

THX for help ;)

---

### Post by imagine on 2006-06-20
Did you use the server install CD? If so then try the alternate install CD and pick "server install" there. This should install an i386-kernel, because your CPU can't handle kernels built for i686 and above.

---

### Post by dixon on 2006-06-20
Yes, I did use the server install CD. I'll try the alternate CD - thx for help ;)

---

### Post by dixon on 2006-06-21
It's working with the alternate CD - THX again ;)

---

### Post by houstonbofh on 2006-06-21
[QUOTE=imagine]Did you use the server install CD? If so then try the alternate install CD and pick "server install" there. This should install an i386-kernel, because your CPU can't handle kernels built for i686 and above.[/QUOTE]
For the future, if you go into the Gurb menu, it should have 386 kernels as a choice.  Then when you come up (or with a rescue disk) you can remove the 686 kernel options.

---

