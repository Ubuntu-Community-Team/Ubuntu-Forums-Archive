---
title: "raid5 resync/rebuild holds boot until completed"
date: 2005-05-17
forum: Server Platforms
---

### Post by bkuhn on 2005-05-17
I first noticed this problem when I rebooted after my first install with a SOFTWARE RAID-5 array set as my root file partition (i.e., /).  The problem is that it appears Ubuntu must do a full resync and rebuild of the RAID5 array before continuing the boot process.  If the RAID array is in degraded mode while booting, I get a message like this at the very start of the boot sequence:

Uncompressing Linux... Ok, booting the kernel.
audit(XXX): initialized.
Starting Ubuntu...
raid5: raid level 5 set md1 active with 3 out of 4 devices, algorithm 2.
mdadm: /devfs/md/1 has been started with 3 drives (out of 4) and 1 spare.
   stopping tasks failed (1 tasks remaining)

It then proceeds to sit and rebuild/resync the RAID array before continuing with the boot process.  This seems bizarre to me.  In other distributions, including stock Debian, the system would boot in degraded mode, with the RAID array being slow, and then rebuild over time.

Does anyone have any suggestions on how to stop this from happening?  It happens even on the initial install onto a large RAID 5 array, since the first reboot during the install process happens before the resync of the array can complete.

---

### Post by valthonis on 2005-05-17
A ha!  So *that's* what it does!  I've been having the same issue.  Software RAID 5 on a dual P3/500.  Of course, it's slow, but the machine stalls for about an hour every reboot to rebuild the array.  Searches of these boards result in very little help.  Can someone address this, or should we just go back to Debian for now?

---

### Post by alastair on 2005-05-17
Hmmm. I have a s/w RAID 1 root disk (/,/boot,/home etc.) and this doesn't happen. 

The RAID starts degraded and I have to manually add the missing device back into the MD device to start the rebuild once I am logged in.

I had to test the behaviour with one of the 2 disks unplugged (tested each).

I'd rather the rebuild occurs automatically as well (but have not researched why not yet).

---

### Post by bkuhn on 2005-05-17
Actually, I misunderstood what was happening.  When the "stopping tasks failed" appears, that's a message from ACPI, not related to the RAID.  It appears that this is some strange interaction bug between Linux's auto-start of the RAID resync and ACPI.

When I set acpi=off in the Linux boot string, all is well.  I'll have to investigate further to see what else can be done.

---

### Post by bkuhn on 2005-05-17
[I have sumbitted a bug over on ubuntulinux.org's bugzilla](https://bugzilla.ubuntu.com/show_bug.cgi?id=10916) ; I expect further discussion will happen on the bugzilla ticket there.

---

### Post by alastair on 2005-05-18
I looked at the source and "Stopping tasks" comes from :

kernel/power/process.c

and function freeze_processes(..).

The file is described as "Functions for starting/stopping processes on suspend transitions". So ACPI is a good guess.

If you have the time/capability, it's the sort of thing you might want to test by building your own kernel, latest source plus patches from the ACPI tree perhaps. OR mention on the kernel list.

---

