---
title: "Lubuntu and Xubuntu (but not Ubuntu) Eoan boot slowly"
date: 2019-10-16
forum: Ubuntu Development Version
---

### Post by sudodus on 2019-10-16
There is a 1 min 30 second delay when booting the current Lubuntu and Xubuntu Eoan live. I did not experience that 9 days ago, and not with the current Ubuntu desktop iso file.

I wrote a bug report about it, but I am not sure, that I have found the cause of the problem (the program package).

Please have a look at [**this bug report**](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1848333) and please test if it affects you too.

---

### Post by PaulW2U on 2019-10-16
Hi  sudodus, I'm on a mobile at the moment so I can't check but I did notice that boot times were rather slow for several flavours when I was testing last night.  I can't remember which flavours though. As the laptop that I use for testing is an inferior Toshiba C50B I'm used to slow boot times anyway. :)

I'll check for you later and will report back if I find anything useful.

---

### Post by sisco311 on 2019-10-16
I would check out the output of:
```
systemd-analyze blame
```

---

### Post by sudodus on 2019-10-16
Here it is, but it does not reflect the 1 min 30 sec delay time. The problem is somewhere else.

```

$ **[COLOR="#008000"]cat systemd-analyze_blame.txt[/COLOR]**
         36.831s systemd-time-wait-sync.service
          3.995s dev-sdc1.device
          3.800s NetworkManager-wait-online.service
          2.526s e2scrub_reap.service
          1.974s dev-loop0.device
          1.954s udisks2.service
          1.851s upower.service
          1.838s dev-zram1.device
          1.808s dev-zram2.device
          1.753s dev-zram0.device
          1.704s networkd-dispatcher.service
          1.696s snapd.service
          1.669s dev-zram3.device
          1.454s ModemManager.service
          1.282s accounts-daemon.service
          1.077s rtkit-daemon.service
          1.076s systemd-logind.service
          1.072s NetworkManager.service
          1.053s rsyslog.service
           990ms systemd-resolved.service
           937ms apport.service
           819ms zram-config.service
           785ms gpu-manager.service
           751ms systemd-networkd.service
           733ms secureboot-db.service
           707ms wpa_supplicant.service
           693ms grub-common.service
           542ms grub-initrd-fallback.service
           533ms thermald.service
           519ms pppd-dns.service
           483ms ofono.service
           417ms systemd-journald.service
           291ms systemd-timesyncd.service
           290ms systemd-update-utmp.service
           187ms keyboard-setup.service
           165ms polkit.service
           164ms snapd.hold.service
           152ms systemd-udev-trigger.service
           123ms user@999.service
           119ms systemd-modules-load.service
           102ms lvm2-monitor.service
            93ms systemd-udevd.service
            89ms bluetooth.service
            76ms systemd-journal-flush.service
            75ms systemd-backlight@backlight:intel_backlight.service
            69ms systemd-tmpfiles-setup.service
            68ms snapd.seeded.service
            64ms snapd.socket
            62ms kerneloops.service
            59ms systemd-rfkill.service
            48ms kmod-static-nodes.service
            46ms dev-mqueue.mount
            45ms ufw.service
            40ms systemd-remount-fs.service
            33ms sys-kernel-debug.mount
            32ms plymouth-read-write.service
            31ms systemd-sysctl.service
            31ms dev-hugepages.mount
            31ms blk-availability.service
            26ms systemd-sysusers.service
            21ms systemd-networkd-wait-online.service
            18ms user-runtime-dir@999.service
            17ms setvtrgb.service
            16ms sddm.service
            15ms console-setup.service
            14ms plymouth-quit.service
            14ms systemd-tmpfiles-setup-dev.service
            13ms sys-kernel-config.mount
            12ms systemd-update-utmp-runlevel.service
            12ms avahi-daemon.service
            12ms systemd-user-sessions.service
             9ms systemd-random-seed.service
             8ms finalrd.service
             6ms sys-fs-fuse-connections.mount
             4ms tmp.mount
           329us clean-mount-point@media-lubuntu-casper\x2drw.service

```

---

### Post by sudodus on 2019-10-17
This bug is squashed in the current final iso file. It was another manifestation of the ‘Kubuntu bug’ first believed to be in ubiquity, then found to be in casper.

See [this link](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1848333), comments 8 and 9.

---

