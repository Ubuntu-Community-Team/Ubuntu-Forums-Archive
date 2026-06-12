---
title: "Startup instance in Virtualbox freeze the entire Ubuntu"
date: 2018-02-23
forum: Virtualisation
---

### Post by jtodd.fr on 2018-02-23
My kernel is 4.13.0-36-generic, Virtualbox version 5.0.40_Ubuntu r115130, and Ubuntu version is 16.04. 

The problem is after starting a newly created guest os instance. Then the entire Ubuntu just freezes (Everything hangs including keyboard mouse). The only way to get back is to reboot - pressing power button to go off system and press again to start from grub. 

Checking /var/log/syslog doesn't find any suspicious virtualbox info or error.
```

Feb 23 14:50:30 host1 virtualbox[19951]:  * Unloading VirtualBox kernel modules...
Feb 23 14:50:30 host1 kernel: [ 1912.462418] VBoxPciLinuxLinuxUnload
Feb 23 14:50:30 host1 virtualbox[19951]:    ...done.
Feb 23 14:50:30 host1 systemd[1]: Stopped LSB: VirtualBox Linux kernel module.
Feb 23 14:50:30 host1 systemd[1]: Starting LSB: VirtualBox Linux kernel module...
Feb 23 14:50:30 host1 virtualbox[19987]:  * Loading VirtualBox kernel modules...
Feb 23 14:50:30 host1 kernel: [ 1912.615522] vboxdrv: Found 8 processor cores
Feb 23 14:50:30 host1 kernel: [ 1912.633598] vboxdrv: TSC mode is Invariant, tentative frequency 2903995619 Hz
Feb 23 14:50:30 host1 kernel: [ 1912.633600] vboxdrv: Successfully loaded version 5.0.40_Ubuntu (interface 0x0024000
0)
Feb 23 14:50:30 host1 kernel: [ 1912.640963] VBoxNetFlt: Successfully started.
Feb 23 14:50:30 host1 kernel: [ 1912.646986] VBoxNetAdp: Successfully started.
Feb 23 14:50:30 host1 kernel: [ 1912.652983] VBoxPciLinuxInit
Feb 23 14:50:30 host1 virtualbox[19987]:    ...done.

```

Nor EE in /var/log/Xorg.0.log file.
Are there any log files that I can check as well? How can I debug to solve this problem?

---

### Post by vasa1 on 2018-02-23
I'm guessing you need to use a newer version of VirtualBox.

See [https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26](https://askubuntu.com/questions/994315/virtualbox-crash-on-kernel-4-13-0-26)

---

### Post by cruzer001 on 2018-02-23
5.2 is working for me.  Watch out for this:
> Important: The Guest Additions which come with VirtualBox 5.2.6 and 5.1.32 do not work properly on Linux guests with 3D enabled.
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

