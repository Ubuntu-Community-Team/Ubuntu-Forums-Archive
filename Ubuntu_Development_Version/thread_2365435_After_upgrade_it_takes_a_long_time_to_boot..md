---
title: "After upgrade it takes a long time to boot."
date: 2017-07-06
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-07-06
This is what I get after a upgrade.

$ systemd-analyze
Bootup is not yet finished. Please try again later.

Try again,

$ systemd-analyze
Startup finished in 10.967s (kernel) + 3min 2.824s (userspace) = 3min 13.791s

```
10.915s dev-sda6.device
          6.459s NetworkManager-wait-online.service
          6.304s ModemManager.service
          5.107s apparmor.service
          3.977s NetworkManager.service
          3.221s gpu-manager.service
          2.789s accounts-daemon.service
          2.506s polkit.service
          2.358s rsyslog.service
          2.118s upower.service
          1.907s keyboard-setup.service
          1.904s avahi-daemon.service
          1.587s grub-common.service
          1.388s plymouth-read-write.service
          1.357s irqbalance.service
          1.172s apport.service
          1.126s systemd-udevd.service
           956ms networking.service
           920ms systemd-tmpfiles-setup.service
           892ms systemd-modules-load.service
           874ms systemd-timesyncd.service
           827ms bluetooth.service
           816ms systemd-rfkill.service
           792ms resolvconf.service
           791ms wpa_supplicant.service
           770ms systemd-tmpfiles-setup-dev.service
           736ms systemd-logind.service
           735ms lightdm.service
           732ms plymouth-quit-wait.service
           703ms systemd-resolved.service
           698ms systemd-update-utmp.service
           600ms systemd-backlight@backlight:acpi_video0.service
           394ms systemd-journal-flush.service
           369ms systemd-udev-trigger.service
           354ms systemd-user-sessions.service
           340ms kerneloops.service
           330ms systemd-journald.service
           315ms plymouth-start.service
           308ms alsa-restore.service
           303ms snapd.autoimport.service
           302ms pppd-dns.service
           268ms setvtrgb.service
           237ms rtkit-daemon.service
           212ms systemd-sysctl.service
           211ms console-setup.service
           175ms sys-kernel-debug.mount
           175ms dev-mqueue.mount
           173ms dev-hugepages.mount
           159ms kmod-static-nodes.service
           113ms udisks2.service
           100ms ufw.service
            99ms systemd-random-seed.service
            85ms user@1000.service
            68ms systemd-remount-fs.service
            11ms ureadahead-stop.service
             5ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount
           591us snapd.socket


```

What might be the problem? the userspace taking so much time.

---

### Post by Chanath on 2017-07-06
Found the answer. The correct swap UUID wasn't written to /etc/fstab. Found the swap UUID through blkid and manually corrected it. Boots normally now.

---

### Post by cariboo on 2017-07-06
> **Chanath said:**
> Found the answer. The correct swap UUID wasn't written to /etc/fstab. Found the swap UUID through blkid and manually corrected it. Boots normally now.

Just FYI, Ubuntu and derivatives no longer need a swap partition:

```
ls -l
total 2097264
drwxr-xr-x   2 root root      12288 Jul  3 13:00 bin
drwxr-xr-x   4 root root       4096 Jul  4 12:38 boot
drwxr-xr-x   2 root root       4096 Apr  4 14:00 cdrom
drwxr-xr-x  20 root root       4180 Jul  6 13:44 dev
drwxr-xr-x 146 root root      12288 Jul  5 13:40 etc
drwxr-xr-x   4 root root       4096 Apr 12 18:02 home
lrwxrwxrwx   1 root root         33 Jul  3 13:01 initrd.img -> boot/initrd.img-4.10.0-28-generic
lrwxrwxrwx   1 root root         33 Jun 30 15:30 initrd.img.old -> boot/initrd.img-4.10.0-26-generic
drwxr-xr-x  21 root root       4096 Apr 29 13:24 lib
drwxr-xr-x   2 root root       4096 Apr  7 20:34 lib64
drwx------   2 root root      16384 Apr  4 13:56 lost+found
drwxr-xr-x   3 root root       4096 Apr 18 11:01 media
drwxr-xr-x   2 root root       4096 Feb 24 17:53 mnt
drwxr-xr-x   5 root root       4096 Jul  2 13:36 opt
dr-xr-xr-x 194 root root          0 Jul  6 13:44 proc
drwx------   8 root root       4096 May  8 00:29 root
drwxr-xr-x  32 root root        940 Jul  6 14:23 run
drwxr-xr-x   2 root root      12288 Jul  5 12:34 sbin
drwxr-xr-x   2 root root       4096 Feb 17 09:58 snap
drwxr-xr-x   2 root root       4096 Feb 24 17:53 srv
[COLOR="#FF0000"]-rw-------   1 root root 2147483648 Apr  4 13:57 swapfile[/COLOR]
dr-xr-xr-x  13 root root          0 Jul  6 13:44 sys
drwxrwxrwt  13 root root       4096 Jul  6 14:18 tmp
drwxr-xr-x  11 root root       4096 Feb 24 18:01 usr
drwxr-xr-x  14 root root       4096 Feb 24 18:10 var
lrwxrwxrwx   1 root root         30 Jul  3 13:01 vmlinuz -> boot/vmlinuz-4.10.0-28-generic
lrwxrwxrwx   1 root root         30 Jun 30 15:30 vmlinuz.old -> boot/vmlinuz-4.10.0-26-generic
```

---

### Post by Chanath on 2017-07-07
I have a swap partition in one laptop, but not in the other. This problem appeared in the one with swap partition. It is 2GB. In the one without the swap partition (it has 8GM RAM), there is a swapfile. I didn't know about this swapfile. It is ~921MB. This swap file is too big for my liking. I see that yours is 2.1GB. What does this swapfile actually contain?

---

### Post by rrnbtter on 2017-07-07
Greetings,
Ubuntu now uses a swapfile if the swap partition is not present.  I'm still using the swap partition of 5G with 4G of RAM. With a Terabyte HD I see this as a luxury that I can afford. No issues that I'm aware.

---

