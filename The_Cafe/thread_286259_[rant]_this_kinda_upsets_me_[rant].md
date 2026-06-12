---
title: "[rant] this kinda upsets me [/rant]"
date: 2006-10-27
forum: The Cafe
---

### Post by user1397 on 2006-10-27
sorry about this attitude of mine, but i am getting pissed off at edgy.  back when i tried installing the beta version, edgy wouldn't let me restart, as seen in my thread: [http://ubuntuforums.org/showthread.php?t=273400](http://ubuntuforums.org/showthread.php?t=273400)

it was never solved, noone could figure out my problem.  i reinstalled dapper, and the restart actually worked in dapper, unlike edgy.  

so now i upgraded to edgy, using the **gksudo "update-manager" -c** command, but it still won't let me restart, at the shut down bootsplash screen, the bar goes all the way to the left, as if it has done everything, sent the term and kill signals, even my keyboard gets cut off from power at this point.  but it'll stall there, and i have to do a manual reboot to restart it.  does anyone know the reason behind this?

please tell me if and how should i file a bug report on this.

---

### Post by arctic on 2006-10-27
I have read about this problem repeatedly with different distros. It seems as if this is an acpi bug in the newer kernels (2.6.17.X series). I would submit a bugreport. I can verify that this prob exists for some users who use the same kernel series in Mandriva, Debian and Fedora.

---

### Post by user1397 on 2006-10-27
> **arctic said:**
> I have read about this problem repeatedly with different distros. It seems as if this is an acpi bug in the newer kernels (2.6.17.X series). I would submit a bugreport. I can verify that this prob exists for some users who use the same kernel series in Mandriva, Debian and Fedora.i've never filed a bug report, so i have no idea where or how to do it.  okay, i know it's something like launchpad, but i've never done one. :-$

---

### Post by arctic on 2006-10-27
[https://bugzilla.redhat.com/bugzilla/page.cgi?id=redhatfaq.html#howdoienter](https://bugzilla.redhat.com/bugzilla/page.cgi?id=redhatfaq.html#howdoienter)
explains how to submit bugs (what to report and how to report)
Launchpad is here: [https://launchpad.net/](https://launchpad.net/)

---

### Post by user1397 on 2006-10-27
the most frequent suggestion, which is to add **acpi=force** to the end of the kernel line in the /boot/grub/menu.lst file, does not work for me at all.  do you think i could install an older kernel and see how it goes?  or will that damage my system?  or should i compile the new kernel? (i've done it before)

---

### Post by 3rdalbum on 2006-10-27
The problem exists for the PowerPC version - your bug report could be quite valuable in finding out exactly what is causing the known problem for PowerPC and your problem on x86.

---

### Post by user1397 on 2006-10-28
arite here's my bug report: [https://launchpad.net/distros/ubuntu/+source/acpi/+bug/68772](https://launchpad.net/distros/ubuntu/+source/acpi/+bug/68772)

sorry if my bug report sounds lousy, 'tis my first time writing one:)

---

### Post by user1397 on 2006-11-14
alright, this problem definitely only affects the 2.6.17 kernel, because i upgraded to feisty, and hence the 2.6.19 kernel, and i'm restarting fine.

yep thats kinda drastic, but feisty is basically edgy right now, with a few more updates, so its pretty stable if you ask me (though it might not be to others)

---

