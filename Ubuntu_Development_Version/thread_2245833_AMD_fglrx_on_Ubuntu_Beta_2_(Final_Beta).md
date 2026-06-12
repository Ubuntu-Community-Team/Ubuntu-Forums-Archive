---
title: "AMD fglrx on Ubuntu Beta 2 (Final Beta)"
date: 2014-09-26
forum: Ubuntu Development Version
---

### Post by csdivad on 2014-09-26
Hi,

I installed the Final Beta of Utopic Unicorn and the fglrx driver with the Additional Drivers program. After a restart only a blank screen welcomed me instead of the desktop. I switched to a terminal and issued "sudo service lightdm restart" and the desktop loaded up fine. If I run "fglrxinfo" it gives this output:

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series
OpenGL version string: 4.4.12968 Compatibility Profile Context 14.201.1006.1002

I guess this indicates that the fglrx is working. I have to restart lightdm on every boot to get to the desktop. I hope this will be fixed in the final release. Is there any quick fix/workaround to this?

(My graphics card: AMD Radeon HD 6950)

---

### Post by Elfy on 2014-09-26
[lpbug]1371651[/lpbug] possibly

No fix yet.

Is this an install in a vm? If it isn't not sure it is that bug.

---

### Post by csdivad on 2014-09-26
No, it isn't installed in a VM.

---

### Post by grahammechanical on 2014-09-30
> [COLOR=#000000]I hope this will be fixed in the final release.[/COLOR]

The fglrx is the proprietary video driver and you are in the same situation as those of us who want to use the Nvidia proprietary driver. If it is incompatible with the kernel that has been installed then the Ubuntu developers cannot do much about it except pass on the bug reports to the owners of the code.

As a work around we can try a different version of the driver. We usually are offered more than one version by Additional Drivers.

Regards.

---

### Post by skeve on 2014-10-01
I solved this problem by editing /etc/default/grub and removing 'quiet splash' options from 'GRUB_CMDLINE_LINUX_DEFAULT=' line.
Don't forget to run update-grub after changing this line.

---

