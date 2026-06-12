---
title: "[SOLVED] after uptade on hardy server, i can no longer reboot"
date: 2008-07-01
forum: Server Platforms
---

### Post by jeantasse on 2008-07-01
After a kernel uptade on hardy server, i can no longer reboot.  The only way i can reboot is by adding the -f option: sudo reboot -f.  The problem after rebooting like that is that it seem to be creating conflic with my quota files.  I can still shutdown, but no reboot.:-k

P.S. Happy Canada day to all Canadians out there!!!!):P

---

### Post by ibutho on 2008-07-01
What happens if you run
```
shutdown -r now
```

---

### Post by jeantasse on 2008-07-02
Thanks, but i get the same message:

* Will now Restart ....   and it freeze there.... i have to do a manual reboot (pressing the button) but it does not break anything since it shutdown propely first

P.S. im french canadian, so my english mith be beurk a bit

---

### Post by ibutho on 2008-07-02
Try booting into the system using the previous kernel you were using before the upgrade (if you did not uninstall it). Does the system reboot properly using that kernel? If that kernel works fine for you, then I suggest you use that for now. There might be something in the new kernel that is not playing nicely with your hardware.

---

### Post by jeantasse on 2008-07-02
The original kernel is 2.6.24-16 and it does the same thing.  Do you know if the "reboot" command can be repaird?

---

### Post by jeantasse on 2008-07-08
thanks anywhay.

---

