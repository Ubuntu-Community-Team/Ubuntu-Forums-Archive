---
title: "Brightness controls not working"
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by Krishna_Manohar on 2014-03-21
Hello,

I understand that you have come across the bug in Ubuntu that the brightness resets to maximum after reboot. I tried these solutions 

[http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25](http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25)   (just used this as given in the 1st answer)

and

[http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart)  (adjusted this to 15 in the rc.local file)

to adjust my default my brightness. But my brightness got very low and besides this my brightness controls are not working. Please let me know the solution on how to fix this problem.

Laptop: Lenovo G460 dual booted Windows7 and Ubuntu 14.04

Thanks,
KM

---

### Post by Krishna_Manohar on 2014-03-21
Could someone reply to this post please. I am being annoyed too much by this.

---

### Post by pqwoerituytrueiwoq on 2014-03-21
here are 2 possible solutions
try doing this
```
~$ cat /etc/default/grub |grep -i windows
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='!Windows 2012'"
```

maybe this script can control the backlight better
[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g)

---

