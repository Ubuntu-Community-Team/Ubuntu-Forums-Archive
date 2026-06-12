---
title: "WINE: Program asking for driver..."
date: 2010-11-11
forum: Wine
---

### Post by LinUxaliVe on 2010-11-11
Hello. I'm running the Ubuntu derivative Lubuntu, but I'd figure it be the same issue.

I've installed the over-clocking software "CPUFSB" through WINE on an older PIII PC. It works just fine through Windows on the same hardware.

I have it installed to "~/.wine/drive_c/Program Files/CPUFSB/CPUFSB.EXE".

When I  initially attempted to run it, I received a message that the "mfc42.dll" was needed, so I copied over the XP version. 

When I ran the program again, this was the message that popped up.

> Please install "NTIOWP.SYS" driver first

Ive checked the "~/.wine/drive_c/windows/system32/drivers" folder, and it is indeed located there. Any ideas why it's asking for it?

BTW - This is on the Lubuntu 10.10 version, and WINE 1.01.

---

### Post by mastablasta on 2010-11-12
you do realize that WINE is not Windows under Linux? it there to help the windows software to be "emulated" by giving them propper windows libraries.
 
so i wouldn't install overclocking software through wine. it would be better to find a linux alternative for that.

---

### Post by gradinaruvasile on 2010-11-12
> **LinUxaliVe said:**
> Hello. I'm running the Ubuntu derivative Lubuntu, but I'd figure it be the same issue.

I've installed the over-clocking software "CPUFSB" through WINE on an older PIII PC. It works just fine through Windows on the same hardware.

I have it installed to "~/.wine/drive_c/Program Files/CPUFSB/CPUFSB.EXE".

When I  initially attempted to run it, I received a message that the "mfc42.dll" was needed, so I copied over the XP version. 

When I ran the program again, this was the message that popped up.



Ive checked the "~/.wine/drive_c/windows/system32/drivers" folder, and it is indeed located there. Any ideas why it's asking for it?

BTW - This is on the Lubuntu 10.10 version, and WINE 1.01.

It will not work. Wine is an emulator and cannot access most low-level functions such as CPU overclocking. No driver will help.

---

### Post by LinUxaliVe on 2010-11-12
I'll uninstall it then.

Thanks. :)

---

