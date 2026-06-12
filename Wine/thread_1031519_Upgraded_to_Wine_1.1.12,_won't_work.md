---
title: "Upgraded to Wine 1.1.12, won't work"
date: 2009-01-05
forum: Wine
---

### Post by rmausser on 2009-01-05
Hi there. I am running Ubuntu Studio 8.10 amd64 on an HP Pavilion dv2000. 

I just recently updated to wine 1.1.12. I use some audio programs like Reaper and Live 7.02 with wineasio and need to have wine working...but also like to keep it at the latest release for hopeful fixes for other software that does not quite yet work. 

Well, after updating now nothing, not even winecfg will open. Programs installed with Crossover or PlayOnLinux that creates separate bottles or wine prefixes still work. 

When I try to open any .exe with wine, or winecfg in terminal(which I believe is written as a windows program) I get this;

fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462740
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x46273c
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462744
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462748
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x46274c
wine: Call from 0x7b845830 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeMutex called at address 0x7b845830 (thread 0014), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.

Please help as I need to use some programs like Live still, and its the only way I can be totally Vista free. 

Thanks everyone.

---

### Post by KeyserSoze93 on 2009-01-05
I had the same errors about ntoskrnl, though it didn't stop me from launching any apps. You should be able to fix this by running ```
wine regedit
```. and finding HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services.

Then delete any keys which mention ntoskrnl.

It appears to be a driver (possibly related to copy protection of some kind) installed with certain apps, which tries to call features of the windows kernel not implemented in wine, but if you take it out of Services, it should be OK....

---

### Post by rmausser on 2009-01-05
Thanks, but when I try to run

wine regedit in terminal I get:

"fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462740
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x46273c
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462744
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x462748
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x46274c
wine: Call from 0x7b845830 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeMutex called at address 0x7b845830 (thread 0014), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart."

So I can't even run reg edit, as I can't run wine to run reg edit!

---

### Post by awillson51 on 2009-01-05
I have pretty much the same problem with 1.1.12.

After compiling and installing wine 1.1.12, I tried to run winecfg.  It took very long to load.  It complained about a wine boot driver of some kind and would not show and virtual drives.

I was able to get winecfg to run error-free with the following sequence:
-make install
-reboot
-make uninstall
-make install

After which winecfg runs...

After attempting to get a few programs running, the wine program seems to have been corupted somehow and presents the exact error depicted above...

System info:
Acer Aspire 5920G
Core 2 Duo T5450
Ubuntu 8.10 (32 bit)

---

### Post by awillson51 on 2009-01-05
Here's the virtual drive error I get:

err:winecfg:open_mountmgr failed to open mount manager err 2

---

