---
title: "Kernel panic'ing, how do i get crash dump to work?"
date: 2015-08-06
forum: Ubuntu Development Version
---

### Post by donbowman on 2015-08-06
[running 15.10 updated today]

Once every 5-10 times, when the machine goes to standby, it will lock up and flash the caps-lock led. I believe this means it has panic'd.

I have followed the recipe [here]("https://wiki.ubuntu.com/Kernel/CrashdumpRecipe") to enable crash dumps, and enabled kdump in /etc/default/kdump-tools.

From X (kde), if i echo c > /proc/sysrq-trigger, it just locks up (flashing caps-lock led), and i don't get a crash dump.
From console, if i trigger a panic, i see the panic message come out, but still don't get a crash dump.

In dmesg i see the crash is enabled:
```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.0-3-generic root=UUID=b646a929-93df-4c72-af66-14bdb33b74cd ro quiet splash crashkernel=384M-:128M vt.handoff=7[    0.000000] Reserving 128MB of memory at 704MB for crashkernel (System RAM: 3797MB)
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.0-3-generic root=UUID=b646a929-93df-4c72-af66-14bdb33b74cd ro quiet splash crashkernel=384M-:128M vt.handoff=7



```

likewise it shows up in grub and the command line:
```
BOOT_IMAGE=/boot/vmlinuz-4.1.0-3-generic root=UUID=b646a929-93df-4c72-af66-14bdb33b74cd ro quiet splash crashkernel=384M-:128M vt.handoff=7


```

This updated as of today, with kernel:
 ```
Linux don-s9 4.1.0-3-generic #3-Ubuntu SMP Tue Jul 28 12:25:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


```

The machine is a samsung n900x3c (series 9), with 4GB ram.

So i guess i'm looking for advice on two things:

1. Why is it panic'ing, how can i avoid this? I'm moderately certain it relates to power management, but not 100%. it does suspend/resume properly some times, and I have seen it panic w/ power plugged in and no reason to be suspending.
2. How do i enable the crash dump to collect this and debug it?

---

### Post by dino99 on 2015-08-06
what i've found with one pc having the same issue: the bios was using the default voltage setting for the ram; and that was the source of plenty kernel panics.
Changing to 'manual' settings for the cpu unhide the ram voltage settings, which i've set to the recommend voltage.
That is, no more kernel panic on my side :p

but there is also an initramfs problem with the latest upgrade (only with newly installed kernel)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1481733](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1481733)

---

### Post by harry332 on 2015-08-06
The bug 1481733 is about kernel panic during en early boot.
Thus prohibiting all other measures than downgrading the previous version of initramfs-tools, which is 0.103ubuntu16.
Chrooting the root partition is necessary to accomplish this.

---

### Post by donbowman on 2015-08-06
yeah i don't think either of those is it.
the machine never panic'd on 13.04/13.10/14.04/14.10/15.04. Its an ultrabook, the ram is soldered to the board, and the bios doesn't expose options for overclocking/undervolting etc. 

Also, that bug id is relating to initramfs, i'm long since past that, the machine is up for hours.

Mostly i'm looking for advice on how to enable the crash dump so i can find the culprit.

---

### Post by cariboo on 2015-08-07
Is there anything in /var/crash pertaining to the problem?

---

