---
title: "What is bare minimum for running multiple virtual computers"
date: 2008-10-08
forum: Virtualisation
---

### Post by abcuser on 2008-10-08
Hi,
on my computer I have Ubuntu 8.04 as host and some of Windows XP and Ubuntus as guests running VirtualBox 2.0.2.

Now I wonder what is the bare minimum to install Ubuntu as host to have as minimal host as possible to consume minimal system resources. So host should be minimal and only capable of running virtual machines and connecting to network.

Now I have Ubuntu 8.04 Desktop as host. Probably Ubuntu 8.04 Server would consume less resources.

Is there any tutorial how to install Ubuntu to consume as minimal resources as possible?
Thanks,
Abcuser

---

### Post by abcuser on 2008-10-08
Hi,
I have found out "Minimal CD Image": [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Is this what I am lookin for?
Regards,
Abcuser

---

### Post by lazyart on 2008-10-08
you probably want Ubuntu JeOS--- Just enough Operating System: [https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)   
The miminalist CD is a net install--- it downloads the packages while you install.

---

### Post by abcuser on 2008-10-08
Hi,
from link you provided there is info that only VMware and KVM are suported.
But I would like to use Sun's VirtualBox.
Regards,
Abcuser

---

### Post by snowpine on 2008-10-08
I've never used JeOS, but actually the instructions in that link seem to be for running JeOS as the *guest* OS, not the *host*, which I think is the opposite of what you want to do.

The Ubuntu Minimal Install CD should work well for your purposes. I believe you'll need to install X and some kind of lightweight windows manager (I like Openbox personally) in order to run VirtualBox. Here's a tutorial: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

edit: ps I am using Crunchbang (which is basically Ubuntu minimal install + Openbox + various apps) and I have no problem running two or more virtual machines on my Pentium 4 with 1.5gb of ram.

---

### Post by UbuWu on 2008-10-08
You can even choose to not install a graphical environment at all and run them as headless machines if you only plan to access them over the network.

---

### Post by abcuser on 2008-10-09
Hi,
what is "headless machines"? Can you point me to some tutorial.
Thanks

---

### Post by lazyart on 2008-10-09
I apologize-- JeOS is actually the opposite of what you wanted.

A headless machine is one with no display.  You access it across the network, usually by ssh and ftp.

---

### Post by lazyart on 2008-10-09
Check my sig.  I just did an install of VMWare Server 2 on a text only host.

---

### Post by abcuser on 2008-10-10
Hi,
thank you very much for advices. I have managed to install Ubuntu (CLI option) from Minimal CD Image. I have installed xorg etc from barebones link posted by snowpine. I have also install OpenBox instead of IceVM as suggested by snowpine. I have also installed VirtualBox from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and I copied virtual-machine images from Windows box to this new Linux box and it works fine!

But now I have one performance question. I am little bit surprised that so much memory is used. I have rebooted Linux and executed "free -m" and result is 127 MB of memory. This is not so little as I have expected. Starting X (startx command) the result is 272 MB this is too much. More then bare Windows XP!

I have executed "ps aux" right after boot and then one more time after startx (please see result bellow). Does anyone see some process that should not be running?

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  2.4  0.1   2844  1688 ?        Ss   08:03   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   08:03   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   08:03   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   08:03   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   08:03   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   08:03   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   08:03   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   08:03   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   08:03   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   08:03   0:00 [kacpi_notify]
root       116  0.0  0.0      0     0 ?        S<   08:03   0:00 [kseriod]
root       150  0.0  0.0      0     0 ?        S    08:03   0:00 [pdflush]
root       151  0.0  0.0      0     0 ?        S    08:03   0:00 [pdflush]
root       152  0.0  0.0      0     0 ?        S<   08:03   0:00 [kswapd0]
root       193  0.0  0.0      0     0 ?        S<   08:03   0:00 [aio/0]
root      1266  0.0  0.0      0     0 ?        S<   08:03   0:00 [ksuspend_usbd]
root      1269  0.0  0.0      0     0 ?        S<   08:03   0:00 [khubd]
root      1356  0.0  0.0      0     0 ?        S<   08:03   0:00 [ata/0]
root      1359  0.0  0.0      0     0 ?        S<   08:03   0:00 [ata_aux]
root      1369  0.0  0.0      0     0 ?        S<   08:03   0:00 [scsi_eh_0]
root      1372  0.0  0.0      0     0 ?        S<   08:03   0:00 [scsi_eh_1]
root      2276  0.0  0.0      0     0 ?        S<   08:03   0:00 [kjournald]
root      2465  0.9  0.0   2224   700 ?        S<s  08:03   0:00 /sbin/udevd --daemon
root      4051  0.0  0.0   1716   512 tty4     Ss+  08:03   0:00 /sbin/getty 38400 tty4
root      4052  0.0  0.0   1716   508 tty5     Ss+  08:03   0:00 /sbin/getty 38400 tty5
root      4057  0.0  0.0   1716   512 tty2     Ss+  08:03   0:00 /sbin/getty 38400 tty2
root      4059  0.0  0.0   1716   512 tty3     Ss+  08:03   0:00 /sbin/getty 38400 tty3
root      4062  0.0  0.0   1716   508 tty6     Ss+  08:03   0:00 /sbin/getty 38400 tty6
root      4207  0.0  0.0   1928   816 ?        Ss   08:03   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    4236  0.0  0.0   1936   648 ?        Ss   08:03   0:00 /sbin/syslogd -u syslog
root      4284  0.1  0.0   1872   540 ?        S    08:03   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4286  0.3  0.1   3168  2000 ?        Ss   08:03   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4309  0.0  0.1   6532  1316 ?        Ss   08:03   0:00 /usr/sbin/nmbd -D
root      4311  0.0  0.2  10108  2304 ?        Ss   08:03   0:00 /usr/sbin/smbd -D
root      4331  0.0  0.1  10108  1036 ?        S    08:03   0:00 /usr/sbin/smbd -D
daemon    4377  0.0  0.0   1984   420 ?        Ss   08:04   0:00 /usr/sbin/atd
root      4388  0.0  0.0   2104   888 ?        Ss   08:04   0:00 /usr/sbin/cron
root      4410  0.0  0.1   2568  1204 tty1     Ss   08:04   0:00 /bin/login --     
igor      4411  0.5  0.2   5432  2848 tty1     S    08:04   0:00 -bash
igor      4430  0.0  0.0   2644  1004 tty1     R+   08:04   0:00 ps aux

```

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  1.0  0.1   2844  1688 ?        Ss   08:03   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   08:03   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   08:03   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   08:03   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   08:03   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   08:03   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   08:03   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   08:03   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   08:03   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   08:03   0:00 [kacpi_notify]
root       116  0.0  0.0      0     0 ?        S<   08:03   0:00 [kseriod]
root       150  0.0  0.0      0     0 ?        S    08:03   0:00 [pdflush]
root       151  0.0  0.0      0     0 ?        S    08:03   0:00 [pdflush]
root       152  0.0  0.0      0     0 ?        S<   08:03   0:00 [kswapd0]
root       193  0.0  0.0      0     0 ?        S<   08:03   0:00 [aio/0]
root      1266  0.0  0.0      0     0 ?        S<   08:03   0:00 [ksuspend_usbd]
root      1269  0.0  0.0      0     0 ?        S<   08:03   0:00 [khubd]
root      1356  0.0  0.0      0     0 ?        S<   08:03   0:00 [ata/0]
root      1359  0.0  0.0      0     0 ?        S<   08:03   0:00 [ata_aux]
root      1369  0.0  0.0      0     0 ?        S<   08:03   0:00 [scsi_eh_0]
root      1372  0.0  0.0      0     0 ?        S<   08:03   0:00 [scsi_eh_1]
root      2276  0.0  0.0      0     0 ?        S<   08:03   0:00 [kjournald]
root      2465  0.3  0.0   2224   700 ?        S<s  08:03   0:00 /sbin/udevd --daemon
root      4051  0.0  0.0   1716   512 tty4     Ss+  08:03   0:00 /sbin/getty 38400 tty4
root      4052  0.0  0.0   1716   508 tty5     Ss+  08:03   0:00 /sbin/getty 38400 tty5
root      4057  0.0  0.0   1716   512 tty2     Ss+  08:03   0:00 /sbin/getty 38400 tty2
root      4059  0.0  0.0   1716   512 tty3     Ss+  08:03   0:00 /sbin/getty 38400 tty3
root      4062  0.0  0.0   1716   508 tty6     Ss+  08:03   0:00 /sbin/getty 38400 tty6
root      4207  0.0  0.0   1928   816 ?        Ss   08:03   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    4236  0.0  0.0   1936   648 ?        Ss   08:03   0:00 /sbin/syslogd -u syslog
root      4284  0.0  0.0   1872   540 ?        S    08:03   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4286  0.1  0.1   3168  2000 ?        Ss   08:03   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4309  0.0  0.1   6532  1316 ?        Ss   08:03   0:00 /usr/sbin/nmbd -D
root      4311  0.0  0.2  10108  2304 ?        Ss   08:03   0:00 /usr/sbin/smbd -D
root      4331  0.0  0.1  10108  1036 ?        S    08:03   0:00 /usr/sbin/smbd -D
daemon    4377  0.0  0.0   1984   420 ?        Ss   08:03   0:00 /usr/sbin/atd
root      4388  0.0  0.0   2104   888 ?        Ss   08:03   0:00 /usr/sbin/cron
root      4410  0.0  0.1   2568  1204 tty1     Ss   08:03   0:00 /bin/login --     
igor      4411  0.1  0.2   5432  2848 tty1     S    08:04   0:00 -bash
igor      4431  0.0  0.1   4288  1516 tty1     S+   08:04   0:00 /bin/bash /usr/bin/startx
igor      4448  0.0  0.0   2784   796 tty1     S+   08:04   0:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc -auth /tmp/serverauth.IgxfbP4438
root      4449  0.6  1.0  16680 10584 tty7     Ss+  08:04   0:00 /usr/bin/X11/X -nolisten tcp
igor      4479  0.1  0.8  14576  8676 tty1     S    08:04   0:00 /usr/bin/openbox
igor      4496  0.0  0.0   4480   532 ?        Ss   08:04   0:00 /usr/bin/ssh-agent x-window-manager
igor      4505  0.0  0.4  11272  4976 tty1     S    08:04   0:00 xterm -class UXTerm -title uxterm -u8
igor      4510  0.2  0.2   5428  2844 pts/0    Rs   08:04   0:00 bash
igor      4530  0.0  0.0   2644  1004 pts/0    R+   08:05   0:00 ps aux

```

How to reduce memory consumption?
Regards,
Abcuser

---

### Post by abcuser on 2008-10-10
Hi,
I have rebooted Linux and executed "free -m" command one more time to really double check memory consumption:
```

             total       used       free     shared    buffers     cached
Mem:          1009       ** 128**        881          0          **5**        **101**
-/+ buffers/cache:         21        988
Swap:         1608          0       1608

```
I have 128 MB used, but I have totally overlooked there is 101 MB cached and 5 MB buffers, together is 106 MB of buffers & caches. So 128 MB minus 106 is **22 MB** of memory actually consumed by system the remaining is caches that can be cleaned by system if needed. Am I making right assumption? If this is right I am astonished how little "barebone" Linux consumes memory?
Regards,
Abcuser

---

### Post by abcuser on 2008-10-10
> **lazyart said:**
> A headless machine is one with no display.  You access it across the network, usually by ssh and ftp.
Hi,
I installed startx, synaptic etc just to simplify install & config process after everything is up and running startx will be stopped.

I have found out how to start headless virtual machine in VirtualBox without needing  xorg & gt etc all staff taking cpu & mem consumption. Just a command:
```
VBoxHeadless -startvm "virtual_guest_name" --vrpport 3389
```
is needed. And then from remote computer remote desktop program to connect to server is required. It is working without any problem.
Thanks for help,
Abcuser

---

### Post by x0as on 2008-10-11
> **abcuser said:**
> Hi,
I have rebooted Linux and executed "free -m" command one more time to really double check memory consumption:
```

             total       used       free     shared    buffers     cached
Mem:          1009       ** 128**        881          0          **5**        **101**
-/+ buffers/cache:         21        988
Swap:         1608          0       1608

```
I have 128 MB used, but I have totally overlooked there is 101 MB cached and 5 MB buffers, together is 106 MB of buffers & caches. So 128 MB minus 106 is **22 MB** of memory actually consumed by system the remaining is caches that can be cleaned by system if needed. Am I making right assumption? If this is right I am astonished how little "barebone" Linux consumes memory?
Regards,
Abcuser

Yep that's right & a barebone debain install uses even less.  This will a be vm box when the rest of the ram turns up.  

```

             total       used       free     shared    buffers     cached
Mem:           123         68         55          0          0         58
-/+ buffers/cache:          9        114
Swap:         2999          0       2999

```

---

