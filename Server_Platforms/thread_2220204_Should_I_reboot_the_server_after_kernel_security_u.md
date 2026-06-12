---
title: "Should I reboot the server after kernel security update?"
date: 2014-04-27
forum: Server Platforms
---

### Post by Adonosonix on 2014-04-27
Hi,

I did 

```
# aptitude update
#aptitude upgrade

```

I got this :

```
The following NEW packages will be installed:
  linux-image-3.2.0-61-generic{a} 
The following packages will be upgraded:
  libcups2 libcupsimage2 linux-firmware linux-image-server linux-libc-dev 

```

Should I reboot my server after a kernel security update ? I guess I should because the old insecure kernel is still running, but I prefer to ask those who know about it, since in my case, rebooting will lead to a temporary interruption of service.



```
 aptitude upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  linux-image-3.2.0-61-generic{a} 
The following packages will be upgraded:
  libcups2 libcupsimage2 linux-firmware linux-image-server linux-libc-dev 
5 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.5 MB of archives. After unpacking 150 MB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2 amd64 1.5.3-0ubuntu8.2 [171 kB]
Get: 2 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsimage2 amd64 1.5.3-0ubuntu8.2 [51.7 kB]
Get: 3 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-61-generic amd64 3.2.0-61.92 [38.7 MB]
Get: 4 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main linux-firmware all 1.79.12 [27.7 MB]                                                                        
Get: 5 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-server amd64 3.2.0.61.72 [2,412 B]                                                              
Get: 6 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main linux-libc-dev amd64 3.2.0-61.92 [860 kB]
Fetched 67.5 MB in 12s (5,291 kB/s)                                                                                                                                          
Reading changelogs... Done
apt-listchanges: Mailing root: apt-listchanges: changelogs for server1.sneakstop.com
(Reading database ... 57945 files and directories currently installed.)
Preparing to replace libcups2 1.5.3-0ubuntu8 (using .../libcups2_1.5.3-0ubuntu8.2_amd64.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace libcupsimage2 1.5.3-0ubuntu8 (using .../libcupsimage2_1.5.3-0ubuntu8.2_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
Selecting previously unselected package linux-image-3.2.0-61-generic.
Unpacking linux-image-3.2.0-61-generic (from .../linux-image-3.2.0-61-generic_3.2.0-61.92_amd64.deb) ...
Done.
Preparing to replace linux-firmware 1.79.11 (using .../linux-firmware_1.79.12_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace linux-image-server 3.2.0.60.71 (using .../linux-image-server_3.2.0.61.72_amd64.deb) ...
Unpacking replacement linux-image-server ...
Preparing to replace linux-libc-dev 3.2.0-60.91 (using .../linux-libc-dev_3.2.0-61.92_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up libcups2 (1.5.3-0ubuntu8.2) ...
Setting up libcupsimage2 (1.5.3-0ubuntu8.2) ...
Setting up linux-image-3.2.0-61-generic (3.2.0-61.92) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-61-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
  No volume groups found
done
Setting up linux-firmware (1.79.12) ...
Setting up linux-image-server (3.2.0.61.72) ...
Setting up linux-libc-dev (3.2.0-61.92) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 updates [-5].
You have new mail in /var/mail/root

```

---

### Post by Gyokuro on 2014-04-28
To make use of the fixed security issues you must restart your server otherwise you are at risk that someone is able to make use of these vulnerabilities - most companies have scheduled update downtimes of their servers. However this can change in case of security issues.

---

### Post by Adonosonix on 2014-04-28
Thank you for your reply. I ended up doing so anyway, but now, I know for sure.

---

### Post by LHammonds on 2014-04-29
Keep 2 or 3 of the latest kernels in /boot but be sure to purge the older ones.

For example:

```

ls -l /boot/vm*
-rw------- 1 root root 4983888 Jan  7 17:22 /boot/vmlinuz-3.2.0-59-generic
-rw------- 1 root root 4981616 Feb 18 22:33 /boot/vmlinuz-3.2.0-60-generic
-rw------- 1 root root 4981616 Mar 31 19:13 /boot/vmlinuz-3.2.0-61-generic

```

In this example, I want to get rid of the oldest which is 3.2.0-59

```

apt-get remove linux-image-3.2.0-59-generic

```

LHammonds

---

### Post by sandyd on 2014-04-29
Btw, if you dont want to reboot, check if your server kernel is supported by ksplice (free for Ubuntu)

---

