---
title: "Shutdown freeze -- how to diagnose?"
date: 2012-11-03
forum: Ubuntu Development Version
---

### Post by dawynn on 2012-11-03
Raring will not shutdown.  Gets part of the way through the process, but leaves the power light on.  In order to shutdown my netbook, I have to unplug it and remove the battery.

Any suggestions on how to diagnose what the problem is?

---

### Post by dino99 on 2012-11-03
remove the "splash" into /etc/default/grub then :

```
sudo update-grub
```

and check the services started at launch time, remove the ones you doesn't need (Applications System-Tools Preferences Startup Services)

then reboot, you'll get now the verbose mode that let you see when freeze happen (most of the time users complaint about modemmanager)

maybe your system need some cleanup (deborphan, bleachbit)

---

### Post by Bucky Ball on 2012-11-03
*Posted in error. ;)*

---

### Post by wnelson on 2012-11-03
Is your bios a UEFI bios? If so add noefi to your grub config. This disables runtime services of UEFI.

This will only effect you system when you upgrade grub at any time. You will need to temporarally remove noefi from your grub config.

Walt

---

### Post by dawynn on 2012-11-03
dino99, thank you very much.  I still don't know what was going on, but your suggestion was not only helpful, it fixed the problem.

In case other's are having similar issues...
In /etc/default/grub, I found this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

I found that if I comment out this line entirely, or just change the option to "quiet", my computer will shut down just fine.  But if I use "splash" or "quiet splash", then my computer hangs at shutdown.

Since I don't really need the splash screen, I accept this solution.

---

