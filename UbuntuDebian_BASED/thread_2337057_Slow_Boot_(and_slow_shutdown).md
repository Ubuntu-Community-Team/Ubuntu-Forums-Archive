---
title: "Slow Boot (and slow shutdown)"
date: 2016-09-13
forum: Ubuntu/Debian BASED
---

### Post by suiciwd on 2016-09-13
My elementary OS Loki (based on 16.04) is taking 40 seconds too boot.

**systemd-analyze**
```

Startup finished in 5.505s (firmware) + 3.241s (loader) + 11.379s (kernel) + 18.512s (userspace) = 38.639s

```

**systemd-analyze blame**
```

         11.499s dev-sda6.device
          7.252s apparmor.service
          3.891s systemd-udevd.service
          3.370s NetworkManager.service
          2.611s systemd-cryptsetup@cryptswap1.service
          2.588s lightdm.service
          2.278s thermald.service
          2.205s plymouth-start.service
          2.041s plymouth-read-write.service
           929ms systemd-modules-load.service
           572ms rsyslog.service
           547ms wpa_supplicant.service
           542ms systemd-logind.service
           538ms systemd-backlight@backlight:radeon_bl0.service
           500ms irqbalance.service
           494ms resolvconf.service
           487ms systemd-sysctl.service
           479ms systemd-timesyncd.service
           471ms systemd-update-utmp.service
           410ms kmod-static-nodes.service
           385ms systemd-remount-fs.service
           365ms systemd-random-seed.service
           337ms upower.service
           167ms user@1000.service
           147ms tmp.mount
           127ms polkitd.service
            89ms systemd-udev-trigger.service
            63ms dev-mapper-cryptswap1.swap
            58ms udisks2.service
            46ms colord.service
            45ms systemd-rfkill.service
            28ms ondemand.service
            21ms systemd-user-sessions.service
             8ms ureadahead-stop.service
             7ms systemd-update-utmp-runlevel.service
             6ms rtkit-daemon.service
             3ms rc-local.service
             2ms openvpn.service

```

How can I speed it up ?

Using normal 5400rpm 500GB HDD on an HP Pavilion g7 laptop

---

### Post by howefield on 2016-09-14
Post moved to own thread and to the "*Ubuntu/Debian BASED*" forum.

---

