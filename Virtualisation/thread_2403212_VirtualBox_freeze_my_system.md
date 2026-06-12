---
title: "VirtualBox freeze my system"
date: 2018-10-08
forum: Virtualisation
---

### Post by sed_faster on 2018-10-08
Hello folks,

I have this environment with virtual box:
```

$ uname -a
Linux user 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
$ virtualbox --help
Oracle VM VirtualBox Manager 5.2.10_Ubuntu

```

After I startup a simple VM with Winxp or Win10 my system simply freeze. This situation didn't occur right after the VM startup. This occur more a less 3 minutes after VM started. To solve this I press ctrl+alt+F1 and accessed screen number 1 (command line). After this I press ctrl+alt+F7 and come back my gui (LXDE). After I do this simply but annoying task the system unleashes.

How can I solve this situation?
These values do not always occur, but of the several times the system freezes and I perform the steps I spoke I was able to capture these values: [https://imgur.com/a/4O0aFui](https://imgur.com/a/4O0aFui)

Thanks

---

### Post by TheFu on 2018-10-08
log files? Use journalctl to get the relevant ones using  a timescale.

Years ago, I had an issue with vbox refusing to run on an brand new ubuntu system.  It was lock up the host completely.
That same, exact, hardware has been running kvm + libvirt since about 3 days later 24/7/365 with 10-20 VMs all this time. KVM is maintained by the Linux kernel team, not a 3rd party team. Just sayin', for you consideration.

---

### Post by sed_faster on 2018-11-04
I consulted journalctl but I can't understand what this file has and where I should look:

```

$ journalctl -r
-- Logs begin at Mon 2018-05-28 14:02:16 WEST, end at Mon 2018-11-05 03:51:00 WET. --
nov 05 03:51:00 user systemd[1]: Started Daily apt download activities.
nov 05 03:50:58 user systemd[1]: Starting Daily apt download activities...
nov 05 03:43:53 user systemd-resolved[570]: Server returned error NXDOMAIN, mitigating potential DNS violation DV
nov 05 03:43:39 user kernel: vboxdrv: 0000000000000000 VBoxDDR0.r0
nov 05 03:43:39 user kernel: vboxdrv: 0000000000000000 VMMR0.r0
nov 05 03:43:39 user kernel: SUPR0GipMap: fGetGipCpu=0xb
nov 05 03:43:32 user kernel: EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
nov 05 03:43:32 user udisksd[638]: Mounted /dev/sdc1 (system) at /media/user/VM on behalf of uid 1000
nov 05 03:42:08 user systemd[1]: Started Stop ureadahead data collection.
nov 05 03:42:08 user systemd[1]: Starting Stop ureadahead data collection...
nov 05 03:42:01 user systemd-timesyncd[568]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
nov 05 03:42:00 user systemd-timesyncd[568]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
nov 05 03:41:30 user kernel: random: crng init done
nov 05 03:41:29 user dbus-daemon[1305]: [session uid=1000 pid=1305] Successfully activated service 'com.canonical
nov 05 03:41:29 user dbus-daemon[1305]: [session uid=1000 pid=1305] Activating service name='com.canonical.indica
nov 05 03:41:29 user pulseaudio[1552]: [pulseaudio] pid.c: Daemon already running.
nov 05 03:41:29 user systemd[1276]: Started Virtual filesystem service - GNOME Online Accounts monitor.
nov 05 03:41:29 user dbus-daemon[1305]: [session uid=1000 pid=1305] Successfully activated service 'org.gtk.vfs.G
nov 05 03:41:29 user systemd[1276]: Starting Virtual filesystem service - GNOME Online Accounts monitor...

```

Between nov 05 03:40 and nov 05 03:48 I started VM win 7 and this process, through virtual 5.2.10 crashed 3 times. All times to unlock the system I hat to did this process:

1-Ctrl+F1
2-Ctrl+F7

I changed between a command line and graphic mode. What should I do?
Thanks

---

### Post by mrsmith31012 on 2018-11-07
As this sounds like a problem I had with my own setup (lubuntu 18.04.1 + virtualbox version 5.2.10_Ubuntu r121806), can you please explain in which way your system freezes?
Are you able to move your mouse but clicks are not recognized?

If so, can you please check if your system is back to normal if you hit Host Key (which should be right ctrl if unchanged) + F twice? (First time to enter fullscreen mode of VM + second time to exit fullscreen mode)

If this "revives" your machine than you have probably the same issue as me.

You can try the steps mentioned in this post: [https://ubuntuforums.org/showthread.php?t=2395969&p=13814509#post13814509](https://ubuntuforums.org/showthread.php?t=2395969&p=13814509#post13814509)

Keep me updated if it solves your problem.
Cheers ;)

---

### Post by sed_faster on 2018-11-07
> **mrsmith31012 said:**
> As this sounds like a problem I had with my own setup (lubuntu 18.04.1 + virtualbox version 5.2.10_Ubuntu r121806), can you please explain in which way your system freezes?
Are you able to move your mouse but clicks are not recognized?

If so, can you please check if your system is back to normal if you hit Host Key (which should be right ctrl if unchanged) + F twice? (First time to enter fullscreen mode of VM + second time to exit fullscreen mode)

If this "revives" your machine than you have probably the same issue as me.

You can try the steps mentioned in this post: [https://ubuntuforums.org/showthread.php?t=2395969&p=13814509#post13814509](https://ubuntuforums.org/showthread.php?t=2395969&p=13814509#post13814509)

Keep me updated if it solves your problem.
Cheers ;)

You saved my life :) Thanks very much! I really need work with VM to emule Windows7 machines and this situation was really be confusing.
Thank you one more time

---

### Post by mrsmith31012 on 2018-11-08
I'm really glad that my tip helped you! It is quite interesting to see that my workaround also helps other people. =)

You are very much welcome ;)

---

