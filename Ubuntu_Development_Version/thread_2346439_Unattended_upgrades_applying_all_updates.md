---
title: "Unattended upgrades applying all updates"
date: 2016-12-14
forum: Ubuntu Development Version
---

### Post by jbicha on 2016-12-14
For those using zesty who want to more carefully apply updates...

It looks like zesty's unattended-upgrades is currently updating all packages automatically. The tracking bug is [1649709]("https://launchpad.net/bugs/1649709")

From my understanding of comment #4, I'm guessing it does not automatically install updates from -proposed for those who like "extra excitement" and have that enabled.


Also, I don't use Lubuntu but apparently if you try to install Lubuntu zesty, you'll be left without grub! [1649462]("https://launchpad.net/bugs/1649462") UPDATE: should be fixed now

---

### Post by jbicha on 2017-05-18
This should be fixed now with this update:

[https://launchpad.net/ubuntu/+source/unattended-upgrades/0.93.1ubuntu6](https://launchpad.net/ubuntu/+source/unattended-upgrades/0.93.1ubuntu6)

---

### Post by dino99 on 2017-05-19
Feedback from Artful

"Automatically check for updates" is set to "Never"  (Software & updates)
but each opened session still "check for updates" automatically on a daily basis
Looks like this "update script" is not unique, or some config setting is not cleaned up when that option is changed.

---

### Post by ventrical on 2017-05-20
But it is not affecting user_space. On gnome-desktop-session (artful) it will notify that updates are available.. so it is not a real hindarance.

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze blame
         14.013s plymouth-quit-wait.service
         11.813s dev-sda5.device
          9.045s apt-daily.service
          7.916s keyboard-setup.service
          7.798s systemd-modules-load.service
          7.489s resolvconf.service
          7.172s systemd-tmpfiles-setup-dev.service
          6.322s NetworkManager-wait-online.service
          6.111s apt-daily-upgrade.service
          3.161s fwupd.service
          2.874s NetworkManager.service
          2.727s grub-common.service
          2.657s ModemManager.service
          2.634s thermald.service
          2.618s lm-sensors.service
          2.385s accounts-daemon.service
          1.956s snapd.autoimport.service
          1.575s networking.service
          1.502s irqbalance.service
          1.365s systemd-logind.service
          1.362s apport.service
          1.291s switcheroo-control.service
          1.290s rtkit-daemon.service
          1.287s gpu-manager.service
          1.286s rsyslog.service
          1.208s systemd-resolved.service
           823ms avahi-daemon.service
           778ms gdm.service
           516ms dev-hugepages.mount
           515ms dev-mqueue.mount
           457ms sys-kernel-debug.mount
           380ms plymouth-start.service
           355ms ufw.service
           315ms systemd-journald.service
           296ms kmod-static-nodes.service
           268ms apparmor.service
           254ms udisks2.service
           235ms systemd-tmpfiles-setup.service
           200ms systemd-hostnamed.service
           184ms swapfile.swap
           153ms systemd-update-utmp.service
           150ms packagekit.service
           134ms systemd-timesyncd.service
           124ms upower.service
           120ms systemd-localed.service
           116ms systemd-remount-fs.service
            90ms polkit.service
            84ms systemd-udevd.service
            72ms systemd-udev-trigger.service
            72ms user@120.service
            70ms speech-dispatcher.service
            60ms user@1000.service
            38ms systemd-journal-flush.service
            36ms wpa_supplicant.service
            35ms setvtrgb.service
            29ms colord.service
            24ms systemd-sysctl.service
            19ms systemd-random-seed.service
            18ms geoclue.service
            17ms pppd-dns.service
            17ms snapd.socket
            11ms plymouth-read-write.service
             9ms hddtemp.service
             7ms systemd-update-utmp-runlevel.service
             5ms ureadahead-stop.service
             5ms console-setup.service
             3ms systemd-user-sessions.service
             2ms sys-fs-fuse-connections.mount
...skipping...
           116ms systemd-remount-fs.service
            90ms polkit.service
            84ms systemd-udevd.service
            72ms systemd-udev-trigger.service
            72ms user@120.service
            70ms speech-dispatcher.service
            60ms user@1000.service
            38ms systemd-journal-flush.service
            36ms wpa_supplicant.service
            35ms setvtrgb.service
            29ms colord.service
            24ms systemd-sysctl.service
            19ms systemd-random-seed.service
            18ms geoclue.service
            17ms pppd-dns.service
            17ms snapd.socket
            11ms plymouth-read-write.service
             9ms hddtemp.service
             7ms systemd-update-utmp-runlevel.service
             5ms ureadahead-stop.service
             5ms console-setup.service
             3ms systemd-user-sessions.service
             2ms sys-fs-fuse-connections.mount
...skipping...
           116ms systemd-remount-fs.service
            90ms polkit.service
            84ms systemd-udevd.service
            72ms systemd-udev-trigger.service
            72ms user@120.service
            70ms speech-dispatcher.service
            60ms user@1000.service
            38ms systemd-journal-flush.service
            36ms wpa_supplicant.service
            35ms setvtrgb.service
            29ms colord.service
            24ms systemd-sysctl.service
            19ms systemd-random-seed.service
            18ms geoclue.service
            17ms pppd-dns.service
            17ms snapd.socket
            11ms plymouth-read-write.service
             9ms hddtemp.service
             7ms systemd-update-utmp-runlevel.service
             5ms ureadahead-stop.service
             5ms console-setup.service
             3ms systemd-user-sessions.service
             2ms sys-fs-fuse-connections.mount

ventrical@ventrical-System-Product-Name:~$ 

```

---

