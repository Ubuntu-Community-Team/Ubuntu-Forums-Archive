---
title: "ubuntu server 12.04.3 and lxde"
date: 2013-11-14
forum: Server Platforms
---

### Post by skinner.clint on 2013-11-14
Hello, I installed lxde for a gui and ever since then when i reboot the machine it boots straight to lxde instead of the server shell. 
How can i revert this ?
any help would be appreciated as I'm fairly new to this.

---

### Post by houstonbofh on 2013-11-15
Remove and purge the desktop manager.  It may be the "lightdm" package, but I do not know what lxde defaults to.

---

### Post by papibe on 2013-11-15
Hi skinner.clint.

If you want to keep LXDE, but to boot into text mode you can do it by editing '/etc/default/grub'. [Here]("http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode")'s how to do it.

Regards.

---

