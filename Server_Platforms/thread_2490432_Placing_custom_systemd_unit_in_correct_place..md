---
title: "Placing custom systemd unit in correct place."
date: 2023-09-04
forum: Server Platforms
---

### Post by carini on 2023-09-04
Good morning,

If my understanding of systemd is correct Distribution-supplied unit file should stay in directory ```
/usr/lib/systemd/system
``` However, unit files are also searched in ```
/usr/lib/systemd/user
``` and ```
/etc/systemd/system
```.

Which is the most correct placement for systemd unit files used to start a custom-developed Node.js service?

---

### Post by LHammonds on 2023-09-04
I cannot speak for anyone else's custom systemd placement but I preferred always using /usr/lib/systemd/system so that everything is in one place.  But I was the primary SSH user of the system.  I would probably sing a different tune if I had to share a server with a dozen other people that might want to make similar changes.

The main thing is to document how "you" configure your system and how "you" deploy services so that others behind you can deploy the same system the same way and achieve the same results.

LHammonds

---

### Post by ian-weisser on 2023-09-04
@LHammonds, as usual, offers great advice. Listen to it.

I put mine in /etc/systemd/system, because that's the directory I backup/restore.

/etc/systemd/system files overrride the similarly-named package-manager-placed files in /usr/lib/systemd/system, so I see no need to modify files in the latter location.
This concept of overriding keeps the package management clean, and ensures that your changes are not overwritten by a package upgrade.

But that's me. You do what works for you.

---

### Post by Doug S on 2023-09-05
I put mine in /etc/systemd/system.
I never make any system changes without a master copy first in my home directory, including an original copy of what has been modified and copies of previous versions. Examples:

```

doug@s19:~$ ls -l config/etc/systemd/system
total 12
-rw-rw-r-- 1 doug doug 187 May 27  2022 doug-post-boot-s19.service
-rw-rw-r-- 1 doug doug 151 May 27  2022 doug-post-boot-s19.service.001
-rw-rw-r-- 1 doug doug 187 May 27  2022 doug-post-boot-s19.service.002
doug@s19:~$ ls -l config/etc/ssh
total 24
-rw-r--r-- 1 doug doug 3320 Dec 19  2021 sshd_config
-rw-r--r-- 1 doug doug 3287 Dec 19  2021 sshd_config.001
-rw-r--r-- 1 doug doug 3320 Apr 11  2022 sshd_config.002
-rw-r--r-- 1 doug doug 3318 Dec 19  2021 sshd_config.doug
-rw-r--r-- 1 doug doug 3289 Aug  7  2020 sshd_config.original
-rw-r--r-- 1 doug doug 3288 Aug  8  2020 sshd_config.test

```

---

### Post by carini on 2023-09-05
Thanks all ... so I think that ```
/etc/systemd/system
``` is the correct place ...

---

### Post by MAFoElffen on 2023-09-06
LOL... In the end, you are free to do as you please. It's your machine. Want to hear the background on that, how it is setup, and how it works?

This is from both what I see when I work with them, and from the Doc's...

Well Ubuntu (Canonical) standards do make sense with this (this time, LOL)... Here is how it is, and the logic behind it.
RE: man page 'systemd.unit' for reference ([https://manpages.ubuntu.com/manpages/jammy/en/man5/systemd.unit.5.html](https://manpages.ubuntu.com/manpages/jammy/en/man5/systemd.unit.5.html))

Look at these:
```

mafoelffen@Mikes-B460M:~$ ls -lah /etc/systemd/system/*.service
lrwxrwxrwx 1 root root  42 Nov 18  2022 /etc/systemd/system/dbus-fi.w1.wpa_supplicant1.service -> /lib/systemd/system/wpa_supplicant.service
lrwxrwxrwx 1 root root  37 Nov 18  2022 /etc/systemd/system/dbus-org.bluez.service -> /lib/systemd/system/bluetooth.service
lrwxrwxrwx 1 root root  40 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.Avahi.service -> /lib/systemd/system/avahi-daemon.service
lrwxrwxrwx 1 root root  40 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.ModemManager1.service -> /lib/systemd/system/ModemManager.service
lrwxrwxrwx 1 root root  44 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.network1.service -> /lib/systemd/system/systemd-networkd.service
lrwxrwxrwx 1 root root  53 Nov 20  2022 /etc/systemd/system/dbus-org.freedesktop.nm-dispatcher.service -> /lib/systemd/system/NetworkManager-dispatcher.service
lrwxrwxrwx 1 root root  40 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.oom1.service -> /lib/systemd/system/systemd-oomd.service
lrwxrwxrwx 1 root root  44 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.resolve1.service -> /lib/systemd/system/systemd-resolved.service
lrwxrwxrwx 1 root root  36 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.thermald.service -> /lib/systemd/system/thermald.service
lrwxrwxrwx 1 root root  45 Nov 18  2022 /etc/systemd/system/dbus-org.freedesktop.timesync1.service -> /lib/systemd/system/systemd-timesyncd.service
lrwxrwxrwx 1 root root  35 Jun 29 01:23 /etc/systemd/system/display-manager.service -> /lib/systemd/system/lightdm.service
lrwxrwxrwx 1 root root  41 Apr 18 08:41 /etc/systemd/system/smartd.service -> /lib/systemd/system/smartmontools.service
-rw-r--r-- 1 root root 592 Aug  4 13:00 /etc/systemd/system/snap.canonical-livepatch.canonical-livepatchd.service
lrwxrwxrwx 1 root root  31 Nov 19  2022 /etc/systemd/system/sshd.service -> /lib/systemd/system/ssh.service
lrwxrwxrwx 1 root root   9 Nov 18  2022 /etc/systemd/system/sudo.service -> /dev/null
lrwxrwxrwx 1 root root  35 Nov 18  2022 /etc/systemd/system/syslog.service -> /lib/systemd/system/rsyslog.service
lrwxrwxrwx 1 root root  35 Nov 18  2022 /etc/systemd/system/zed.service -> /lib/systemd/system/zfs-zed.service
mafoelffen@Mikes-B460M:~$ ls -lah /usr/lib/systemd/system/*.service
-rw-r--r-- 1 root root 2.0K Jun 20 04:25 /usr/lib/systemd/system/accounts-daemon.service
-rw-r--r-- 1 root root  261 Jan 25  2022 /usr/lib/systemd/system/acpid.service
-rw-r--r-- 1 root root  613 Jan 12  2022 /usr/lib/systemd/system/alsa-restore.service
-rw-r--r-- 1 root root  565 Jan 12  2022 /usr/lib/systemd/system/alsa-state.service
lrwxrwxrwx 1 root root    9 Nov 18  2022 /usr/lib/systemd/system/alsa-utils.service -> /dev/null
-rw-r--r-- 1 root root  776 Oct  9  2021 /usr/lib/systemd/system/anacron.service
-rw-r--r-- 1 root root 1.2K Feb 23  2022 /usr/lib/systemd/system/apparmor.service
-rw-r--r-- 1 root root  249 Apr 13 16:08 /usr/lib/systemd/system/apport-autoreport.service
-rw-r--r-- 1 root root  142 Nov 11  2019 /usr/lib/systemd/system/apport-forward@.service
-rw-r--r-- 1 root root  326 Oct 31  2022 /usr/lib/systemd/system/apt-daily.service
-rw-r--r-- 1 root root  389 Oct 31  2022 /usr/lib/systemd/system/apt-daily-upgrade.service
-rw-r--r-- 1 root root  747 May 30 11:42 /usr/lib/systemd/system/apt-news.service
-rw-r--r-- 1 root root  706 Oct 20  2022 /usr/lib/systemd/system/auth-rpcgss-module.service
lrwxrwxrwx 1 root root   14 Mar 20 07:32 /usr/lib/systemd/system/autovt@.service -> getty@.service
-rw-r--r-- 1 root root 1.1K May 31 06:57 /usr/lib/systemd/system/avahi-daemon.service
-rw-r--r-- 1 root root  380 Feb 16  2022 /usr/lib/systemd/system/blk-availability.service
-rw-r--r-- 1 root root  702 Mar 23  2022 /usr/lib/systemd/system/bluetooth.service
-rw-r--r-- 1 root root  642 Feb  7  2022 /usr/lib/systemd/system/bolt.service
-rw-r--r-- 1 root root  483 Nov 16  2021 /usr/lib/systemd/system/brltty.service
-rw-r--r-- 1 root root  429 Nov 17  2021 /usr/lib/systemd/system/brltty-udev.service
-rw-r--r-- 1 root root  295 Feb 22  2022 /usr/lib/systemd/system/colord.service
-rw-r--r-- 1 root root  150 Feb 21  2022 /usr/lib/systemd/system/configure-printer@.service
-rw-r--r-- 1 root root 1.1K Mar 20 07:32 /usr/lib/systemd/system/console-getty.service
-rw-r--r-- 1 root root  312 Jul 23  2021 /usr/lib/systemd/system/console-setup.service
-rw-r--r-- 1 root root 1.3K Mar 20 07:32 /usr/lib/systemd/system/container-getty@.service
-rw-r--r-- 1 root root  319 Mar 17  2021 /usr/lib/systemd/system/cron.service
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/cryptdisks-early.service -> /dev/null
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/cryptdisks.service -> /dev/null
-rw-r--r-- 1 root root  278 Apr 11  2022 /usr/lib/systemd/system/cups-browsed.service
-rw-r--r-- 1 root root  292 Jun 13 05:17 /usr/lib/systemd/system/cups.service
lrwxrwxrwx 1 root root   25 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.hostname1.service -> systemd-hostnamed.service
lrwxrwxrwx 1 root root   23 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.import1.service -> systemd-importd.service
lrwxrwxrwx 1 root root   23 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.locale1.service -> systemd-localed.service
lrwxrwxrwx 1 root root   22 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.login1.service -> systemd-logind.service
lrwxrwxrwx 1 root root   24 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.machine1.service -> systemd-machined.service
lrwxrwxrwx 1 root root   25 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.portable1.service -> systemd-portabled.service
lrwxrwxrwx 1 root root   25 Mar 20 07:32 /usr/lib/systemd/system/dbus-org.freedesktop.timedate1.service -> systemd-timedated.service
-rw-r--r-- 1 root root  498 Oct 25  2022 /usr/lib/systemd/system/dbus.service
-rw-r--r-- 1 root root 1.1K Mar 20 07:32 /usr/lib/systemd/system/debug-shell.service
-rw-r--r-- 1 root root  409 Nov 16  2021 /usr/lib/systemd/system/dmesg.service
-rw-r--r-- 1 root root  341 Feb 16  2022 /usr/lib/systemd/system/dm-event.service
-rw-r--r-- 1 root root  147 Dec  5  2021 /usr/lib/systemd/system/dpkg-db-backup.service
-rw-r--r-- 1 root root  297 Jun  1  2022 /usr/lib/systemd/system/e2scrub_all.service
-rw-r--r-- 1 root root  245 Jun  1  2022 /usr/lib/systemd/system/e2scrub_fail@.service
-rw-r--r-- 1 root root  553 Jun  1  2022 /usr/lib/systemd/system/e2scrub_reap.service
-rw-r--r-- 1 root root  438 Jun  1  2022 /usr/lib/systemd/system/e2scrub@.service
-rw-r--r-- 1 root root  805 Mar 20 07:32 /usr/lib/systemd/system/emergency.service
-rw-r--r-- 1 root root  688 May 30 11:42 /usr/lib/systemd/system/esm-cache.service
-rw-r--r-- 1 root root  419 Feb 16  2022 /usr/lib/systemd/system/finalrd.service
-rw-r--r-- 1 root root  236 Oct 28  2021 /usr/lib/systemd/system/fio.service
-rw-r--r-- 1 root root  263 Mar 14  2022 /usr/lib/systemd/system/flatpak-system-helper.service
-rw-r--r-- 1 root root  900 Jul 15  2022 /usr/lib/systemd/system/fprintd.service
-rw-r--r-- 1 root root  618 Oct  2  2018 /usr/lib/systemd/system/friendly-recovery.service
-rw-r--r-- 1 root root  477 Feb 20  2022 /usr/lib/systemd/system/fstrim.service
-rw-r--r-- 1 root root  406 May 16 22:35 /usr/lib/systemd/system/fwupd-offline-update.service
-rw-r--r-- 1 root root  450 May 16 22:35 /usr/lib/systemd/system/fwupd-refresh.service
-rw-r--r-- 1 root root  650 May 16 22:35 /usr/lib/systemd/system/fwupd.service
lrwxrwxrwx 1 root root   11 Jun  1 03:37 /usr/lib/systemd/system/gdm3.service -> gdm.service
-rw-r--r-- 1 root root  982 Jun  1 03:37 /usr/lib/systemd/system/gdm.service
-rw-r--r-- 1 root root  468 Mar 23  2022 /usr/lib/systemd/system/geoclue.service
-rw-r--r-- 1 root root 2.0K Mar 20 07:32 /usr/lib/systemd/system/getty@.service
-rw-r--r-- 1 root root  366 Mar 20 07:32 /usr/lib/systemd/system/getty-static.service
-rw-r--r-- 1 root root  332 Jan  4  2022 /usr/lib/systemd/system/gpu-manager.service
-rw-r--r-- 1 root root  583 Dec  2  2022 /usr/lib/systemd/system/grub-common.service
-rw-r--r-- 1 root root  408 Dec 18  2022 /usr/lib/systemd/system/grub-initrd-fallback.service
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/hwclock.service -> /dev/null
-rw-r--r-- 1 root root  424 Mar 17  2022 /usr/lib/systemd/system/iio-sensor-proxy.service
-rw-r--r-- 1 root root  670 Mar 11  2022 /usr/lib/systemd/system/initrd-cleanup.service
-rw-r--r-- 1 root root  820 Mar 11  2022 /usr/lib/systemd/system/initrd-parse-etc.service
-rw-r--r-- 1 root root  589 Mar 11  2022 /usr/lib/systemd/system/initrd-switch-root.service
-rw-r--r-- 1 root root  823 Mar 11  2022 /usr/lib/systemd/system/initrd-udevadm-cleanup-db.service
-rw-r--r-- 1 root root  207 Apr 27 00:07 /usr/lib/systemd/system/ipp-usb.service
-rw-r--r-- 1 root root  505 Mar 24  2022 /usr/lib/systemd/system/irqbalance.service
-rw-r--r-- 1 root root  376 May 19  2017 /usr/lib/systemd/system/kerneloops.service
-rw-r--r-- 1 root root  287 Jul 23  2021 /usr/lib/systemd/system/keyboard-setup.service
lrwxrwxrwx 1 root root   28 Mar 20 07:32 /usr/lib/systemd/system/kmod.service -> systemd-modules-load.service
-rw-r--r-- 1 root root  701 Mar 20 07:32 /usr/lib/systemd/system/kmod-static-nodes.service
-rw-r--r-- 1 root root 2.0K Jun 19 18:54 /usr/lib/systemd/system/libvirtd.service
-rw-r--r-- 1 root root  623 Jun 19 18:54 /usr/lib/systemd/system/libvirt-guests.service
-rw-r--r-- 1 root root  506 Aug 13  2019 /usr/lib/systemd/system/lightdm.service
-rw-r--r-- 1 root root  199 Mar 31  2022 /usr/lib/systemd/system/lm-sensors.service
-rw-r--r-- 1 root root  870 Aug 21  2020 /usr/lib/systemd/system/logrotate.service
-rw-r--r-- 1 root root  323 Feb 16  2022 /usr/lib/systemd/system/lvm2-lvmpolld.service
-rw-r--r-- 1 root root  602 Feb 16  2022 /usr/lib/systemd/system/lvm2-monitor.service
-rw-r--r-- 1 root root  338 Feb 16  2022 /usr/lib/systemd/system/lvm2-pvscan@.service
lrwxrwxrwx 1 root root    9 Feb 16  2022 /usr/lib/systemd/system/lvm2.service -> /dev/null
-rw-r--r-- 1 root root  738 Mar 17  2022 /usr/lib/systemd/system/man-db.service
-rw-r--r-- 1 root root  508 Apr 10 20:22 /usr/lib/systemd/system/mdadm-grow-continue@.service
-rw-r--r-- 1 root root  237 Apr 10 20:22 /usr/lib/systemd/system/mdadm-last-resort@.service
-rw-r--r-- 1 root root  558 Apr 10 20:22 /usr/lib/systemd/system/mdcheck_continue.service
-rw-r--r-- 1 root root  510 Apr 10 20:22 /usr/lib/systemd/system/mdcheck_start.service
-rw-r--r-- 1 root root  490 Apr 10 20:22 /usr/lib/systemd/system/mdmonitor-oneshot.service
-rw-r--r-- 1 root root  415 Apr 10 20:22 /usr/lib/systemd/system/mdmonitor.service
-rw-r--r-- 1 root root 1.1K Apr 10 20:22 /usr/lib/systemd/system/mdmon@.service
-rw-r--r-- 1 root root  515 Jun 14 01:21 /usr/lib/systemd/system/ModemManager.service
-rw-r--r-- 1 root root  573 Mar 20 07:32 /usr/lib/systemd/system/modprobe@.service
-rw-r--r-- 1 root root  173 Aug  2 06:12 /usr/lib/systemd/system/motd-news.service
-rw-r--r-- 1 root root  258 May  4  2022 /usr/lib/systemd/system/networkd-dispatcher.service
-rw-r--r-- 1 root root  652 Jun  9  2022 /usr/lib/systemd/system/NetworkManager-dispatcher.service
-rw-r--r-- 1 root root 1.4K Jun  9  2022 /usr/lib/systemd/system/NetworkManager.service
-rw-r--r-- 1 root root 1.2K Jun  9  2022 /usr/lib/systemd/system/NetworkManager-wait-online.service
-rw-r--r-- 1 root root  291 Oct 20  2022 /usr/lib/systemd/system/nfs-blkmap.service
lrwxrwxrwx 1 root root    9 Oct 20  2022 /usr/lib/systemd/system/nfs-common.service -> /dev/null
-rw-r--r-- 1 root root  236 Oct 20  2022 /usr/lib/systemd/system/nfsdcld.service
-rw-r--r-- 1 root root  222 Oct 20  2022 /usr/lib/systemd/system/nfs-idmapd.service
lrwxrwxrwx 1 root root   18 Oct 20  2022 /usr/lib/systemd/system/nfs-kernel-server.service -> nfs-server.service
-rw-r--r-- 1 root root  287 Oct 20  2022 /usr/lib/systemd/system/nfs-mountd.service
-rw-r--r-- 1 root root  895 Oct 20  2022 /usr/lib/systemd/system/nfs-server.service
-rw-r--r-- 1 root root  567 Oct 20  2022 /usr/lib/systemd/system/nfs-utils.service
-rw-r--r-- 1 root root  458 Mar 23  2022 /usr/lib/systemd/system/nftables.service
-rw-r--r-- 1 root root 2.1K Jun  9  2022 /usr/lib/systemd/system/nm-priv-helper.service
-rw-r--r-- 1 root root  284 Nov  8  2022 /usr/lib/systemd/system/nvmefc-boot-connections.service
-rw-r--r-- 1 root root  310 Nov  8  2022 /usr/lib/systemd/system/nvmf-autoconnect.service
-rw-r--r-- 1 root root  333 Nov  8  2022 /usr/lib/systemd/system/nvmf-connect@.service
-rw-r--r-- 1 root root  688 Jul 14  2022 /usr/lib/systemd/system/openvpn-client@.service
-rw-r--r-- 1 root root  810 Jul 14  2022 /usr/lib/systemd/system/openvpn-server@.service
-rw-r--r-- 1 root root  299 Jun 14  2022 /usr/lib/systemd/system/openvpn.service
-rw-r--r-- 1 root root  946 Jun 14  2022 /usr/lib/systemd/system/openvpn@.service
-rw-r--r-- 1 root root  400 Mar 14  2022 /usr/lib/systemd/system/packagekit-offline-update.service
-rw-r--r-- 1 root root  392 Mar 14  2022 /usr/lib/systemd/system/packagekit.service
-rw-r--r-- 1 root root  475 Mar 18  2022 /usr/lib/systemd/system/plymouth-halt.service
-rw-r--r-- 1 root root  489 Mar 18  2022 /usr/lib/systemd/system/plymouth-kexec.service
lrwxrwxrwx 1 root root   27 Nov 18  2022 /usr/lib/systemd/system/plymouth-log.service -> plymouth-read-write.service
-rw-r--r-- 1 root root  484 Mar 18  2022 /usr/lib/systemd/system/plymouth-poweroff.service
-rw-r--r-- 1 root root  218 Mar 18  2022 /usr/lib/systemd/system/plymouth-quit.service
-rw-r--r-- 1 root root  224 Mar 18  2022 /usr/lib/systemd/system/plymouth-quit-wait.service
-rw-r--r-- 1 root root  268 Mar 18  2022 /usr/lib/systemd/system/plymouth-read-write.service
-rw-r--r-- 1 root root  477 Mar 18  2022 /usr/lib/systemd/system/plymouth-reboot.service
lrwxrwxrwx 1 root root   21 Nov 18  2022 /usr/lib/systemd/system/plymouth.service -> plymouth-quit.service
-rw-r--r-- 1 root root  617 Mar 18  2022 /usr/lib/systemd/system/plymouth-start.service
-rw-r--r-- 1 root root  894 Mar 18  2022 /usr/lib/systemd/system/plymouth-switch-root-initramfs.service
-rw-r--r-- 1 root root  315 Mar 18  2022 /usr/lib/systemd/system/plymouth-switch-root.service
-rw-r--r-- 1 root root  167 Feb 26  2022 /usr/lib/systemd/system/polkit.service
lrwxrwxrwx 1 root root   15 Feb 16  2022 /usr/lib/systemd/system/portmap.service -> rpcbind.service
-rw-r--r-- 1 root root  697 Mar  5  2022 /usr/lib/systemd/system/power-profiles-daemon.service
lrwxrwxrwx 1 root root   22 Mar 20 07:32 /usr/lib/systemd/system/procps.service -> systemd-sysctl.service
lrwxrwxrwx 1 root root    9 Feb 15  2023 /usr/lib/systemd/system/pulseaudio-enable-autospawn.service -> /dev/null
-rw-r--r-- 1 root root  367 Jan  5  2021 /usr/lib/systemd/system/qemu-kvm.service
-rw-r--r-- 1 root root  617 Mar 20 07:32 /usr/lib/systemd/system/quotaon.service
-rw-r--r-- 1 root root  724 Mar 20 07:32 /usr/lib/systemd/system/rc-local.service
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/rc.service -> /dev/null
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/rcS.service -> /dev/null
-rw-r--r-- 1 root root  796 Mar 20 07:32 /usr/lib/systemd/system/rescue.service
-rw-r--r-- 1 root root  626 Aug 17  2021 /usr/lib/systemd/system/rpcbind.service
-rw-r--r-- 1 root root  281 Oct 20  2022 /usr/lib/systemd/system/rpc-gssd.service
-rw-r--r-- 1 root root  383 Oct 20  2022 /usr/lib/systemd/system/rpc-statd-notify.service
-rw-r--r-- 1 root root  425 Oct 20  2022 /usr/lib/systemd/system/rpc-statd.service
-rw-r--r-- 1 root root  358 Oct 20  2022 /usr/lib/systemd/system/rpc-svcgssd.service
-rw-r--r-- 1 root root 1.1K Apr 11  2022 /usr/lib/systemd/system/rsync.service
-rw-r--r-- 1 root root  469 Dec 23  2021 /usr/lib/systemd/system/rsyslog.service
-rw-r--r-- 1 root root 1.0K Mar 25  2022 /usr/lib/systemd/system/rtkit-daemon.service
lrwxrwxrwx 1 root root    9 Nov 18  2022 /usr/lib/systemd/system/saned.service -> /dev/null
-rw-r--r-- 1 root root  347 Sep 10  2020 /usr/lib/systemd/system/saned@.service
-rw-r--r-- 1 root root  735 Aug 26  2020 /usr/lib/systemd/system/secureboot-db.service
-rw-r--r-- 1 root root  371 Nov  8  2021 /usr/lib/systemd/system/selinux-autorelabel-mark.service
-rw-r--r-- 1 root root  280 Nov  8  2021 /usr/lib/systemd/system/selinux-autorelabel.service
-rw-r--r-- 1 root root 1.5K Mar 20 07:32 /usr/lib/systemd/system/serial-getty@.service
-rw-r--r-- 1 root root  330 Nov 27  2019 /usr/lib/systemd/system/setvtrgb.service
-rw-r--r-- 1 root root  353 Mar 25  2022 /usr/lib/systemd/system/smartmontools.service
-rw-r--r-- 1 root root  297 May 29 05:08 /usr/lib/systemd/system/snapd.aa-prompt-listener.service
-rw-r--r-- 1 root root  880 May 29 05:08 /usr/lib/systemd/system/snapd.apparmor.service
-rw-r--r-- 1 root root  432 May 29 05:08 /usr/lib/systemd/system/snapd.autoimport.service
-rw-r--r-- 1 root root  369 May 29 05:08 /usr/lib/systemd/system/snapd.core-fixup.service
-rw-r--r-- 1 root root  151 May 29 05:08 /usr/lib/systemd/system/snapd.failure.service
-rw-r--r-- 1 root root  550 May 29 05:08 /usr/lib/systemd/system/snapd.recovery-chooser-trigger.service
-rw-r--r-- 1 root root  322 May 29 05:08 /usr/lib/systemd/system/snapd.seeded.service
-rw-r--r-- 1 root root  590 May 29 05:08 /usr/lib/systemd/system/snapd.service
-rw-r--r-- 1 root root  421 May 29 05:08 /usr/lib/systemd/system/snapd.snap-repair.service
-rw-r--r-- 1 root root  608 May 29 05:08 /usr/lib/systemd/system/snapd.system-shutdown.service
-rw-r--r-- 1 root root 1.1K May 23 00:29 /usr/lib/systemd/system/speech-dispatcherd.service
-rw-r--r-- 1 root root  331 Feb 24  2022 /usr/lib/systemd/system/spice-vdagentd.service
lrwxrwxrwx 1 root root   22 Nov 18  2022 /usr/lib/systemd/system/spice-vdagent.service -> spice-vdagentd.service
-rw-r--r-- 1 root root  538 Nov 14  2022 /usr/lib/systemd/system/ssh.service
-rw-r--r-- 1 root root  318 Nov 14  2022 /usr/lib/systemd/system/ssh@.service
-rw-r--r-- 1 root root  497 Mar 25  2022 /usr/lib/systemd/system/switcheroo-control.service
-rw-r--r-- 1 root root  388 Jun  6 06:27 /usr/lib/systemd/system/sysstat-collect.service
-rw-r--r-- 1 root root  521 Jun  6 06:27 /usr/lib/systemd/system/sysstat.service
-rw-r--r-- 1 root root  368 Jun  6 06:27 /usr/lib/systemd/system/sysstat-summary.service
-rw-r--r-- 1 root root  745 Mar 11  2022 /usr/lib/systemd/system/systemd-ask-password-console.service
-rw-r--r-- 1 root root  502 Mar 18  2022 /usr/lib/systemd/system/systemd-ask-password-plymouth.service
-rw-r--r-- 1 root root  747 Mar 11  2022 /usr/lib/systemd/system/systemd-ask-password-wall.service
-rw-r--r-- 1 root root  727 Mar 20 07:32 /usr/lib/systemd/system/systemd-backlight@.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-binfmt.service
-rw-r--r-- 1 root root  686 Mar 20 07:32 /usr/lib/systemd/system/systemd-bless-boot.service
-rw-r--r-- 1 root root  726 Mar 20 07:32 /usr/lib/systemd/system/systemd-boot-check-no-failures.service
-rw-r--r-- 1 root root 1.4K Mar 11  2022 /usr/lib/systemd/system/systemd-boot-system-token.service
-rw-r--r-- 1 root root  564 Mar 11  2022 /usr/lib/systemd/system/systemd-exit.service
-rw-r--r-- 1 root root  551 Mar 20 07:32 /usr/lib/systemd/system/systemd-fsckd.service
-rw-r--r-- 1 root root  748 Mar 20 07:32 /usr/lib/systemd/system/systemd-fsck-root.service
-rw-r--r-- 1 root root  749 Mar 20 07:32 /usr/lib/systemd/system/systemd-fsck@.service
-rw-r--r-- 1 root root  594 Mar 11  2022 /usr/lib/systemd/system/systemd-halt.service
-rw-r--r-- 1 root root  676 Mar 20 07:32 /usr/lib/systemd/system/systemd-hibernate-resume@.service
-rw-r--r-- 1 root root  551 Mar 20 07:32 /usr/lib/systemd/system/systemd-hibernate.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-hostnamed.service
-rw-r--r-- 1 root root  572 Mar 20 07:32 /usr/lib/systemd/system/systemd-hybrid-sleep.service
-rw-r--r-- 1 root root 1.1K Mar 20 07:32 /usr/lib/systemd/system/systemd-importd.service
-rw-r--r-- 1 root root  574 Mar 20 07:32 /usr/lib/systemd/system/systemd-initctl.service
-rw-r--r-- 1 root root 1.8K Mar 20 07:32 /usr/lib/systemd/system/systemd-journald.service
-rw-r--r-- 1 root root 1.5K Mar 20 07:32 /usr/lib/systemd/system/systemd-journald@.service
-rw-r--r-- 1 root root  819 Mar 11  2022 /usr/lib/systemd/system/systemd-journal-flush.service
-rw-r--r-- 1 root root  601 Mar 11  2022 /usr/lib/systemd/system/systemd-kexec.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-localed.service
-rw-r--r-- 1 root root 2.1K Mar 20 07:32 /usr/lib/systemd/system/systemd-logind.service
-rw-r--r-- 1 root root 1.3K Mar 20 07:32 /usr/lib/systemd/system/systemd-machined.service
-rw-r--r-- 1 root root  748 Mar 11  2022 /usr/lib/systemd/system/systemd-machine-id-commit.service
-rw-r--r-- 1 root root 1.1K Mar 20 07:32 /usr/lib/systemd/system/systemd-modules-load.service
-rw-r--r-- 1 root root 2.3K Mar 20 07:32 /usr/lib/systemd/system/systemd-networkd.service
-rw-r--r-- 1 root root  748 Mar 20 07:32 /usr/lib/systemd/system/systemd-networkd-wait-online.service
-rw-r--r-- 1 root root  686 Mar 20 07:32 /usr/lib/systemd/system/systemd-network-generator.service
-rw-r--r-- 1 root root 1.6K Mar 20 07:32 /usr/lib/systemd/system/systemd-nspawn@.service
-rw-r--r-- 1 root root 1.7K Mar 20 07:32 /usr/lib/systemd/system/systemd-oomd.service
-rw-r--r-- 1 root root 1023 Mar 20 07:32 /usr/lib/systemd/system/systemd-portabled.service
-rw-r--r-- 1 root root  575 Mar 11  2022 /usr/lib/systemd/system/systemd-poweroff.service
-rw-r--r-- 1 root root 1.1K Mar 20 07:32 /usr/lib/systemd/system/systemd-pstore.service
-rw-r--r-- 1 root root  663 Mar 20 07:32 /usr/lib/systemd/system/systemd-quotacheck.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-random-seed.service
-rw-r--r-- 1 root root  568 Mar 11  2022 /usr/lib/systemd/system/systemd-reboot.service
-rw-r--r-- 1 root root  775 Mar 20 07:32 /usr/lib/systemd/system/systemd-remount-fs.service
-rw-r--r-- 1 root root 1.8K Mar 20 07:32 /usr/lib/systemd/system/systemd-resolved.service
-rw-r--r-- 1 root root  725 Mar 20 07:32 /usr/lib/systemd/system/systemd-rfkill.service
-rw-r--r-- 1 root root  552 Mar 20 07:32 /usr/lib/systemd/system/systemd-suspend.service
-rw-r--r-- 1 root root  619 Mar 20 07:32 /usr/lib/systemd/system/systemd-suspend-then-hibernate.service
-rw-r--r-- 1 root root  701 Mar 20 07:32 /usr/lib/systemd/system/systemd-sysctl.service
-rw-r--r-- 1 root root 1002 Mar 11  2022 /usr/lib/systemd/system/systemd-sysext.service
-rw-r--r-- 1 root root 1.0K Mar 11  2022 /usr/lib/systemd/system/systemd-sysusers.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-timedated.service
-rw-r--r-- 1 root root 1.8K Mar 20 07:32 /usr/lib/systemd/system/systemd-timesyncd.service
-rw-r--r-- 1 root root 1.2K Mar 20 07:32 /usr/lib/systemd/system/systemd-time-wait-sync.service
-rw-r--r-- 1 root root  666 Mar 11  2022 /usr/lib/systemd/system/systemd-tmpfiles-clean.service
-rw-r--r-- 1 root root  747 Mar 11  2022 /usr/lib/systemd/system/systemd-tmpfiles-setup-dev.service
-rw-r--r-- 1 root root  787 Mar 11  2022 /usr/lib/systemd/system/systemd-tmpfiles-setup.service
-rw-r--r-- 1 root root 1.3K Mar 20 07:32 /usr/lib/systemd/system/systemd-udevd.service
-rw-r--r-- 1 root root  863 Mar 11  2022 /usr/lib/systemd/system/systemd-udev-settle.service
-rw-r--r-- 1 root root  763 Mar 11  2022 /usr/lib/systemd/system/systemd-udev-trigger.service
-rw-r--r-- 1 root root  803 Mar 20 07:32 /usr/lib/systemd/system/systemd-update-utmp-runlevel.service
-rw-r--r-- 1 root root  799 Mar 20 07:32 /usr/lib/systemd/system/systemd-update-utmp.service
-rw-r--r-- 1 root root  647 Mar 20 07:32 /usr/lib/systemd/system/systemd-user-sessions.service
-rw-r--r-- 1 root root  739 Mar 20 07:32 /usr/lib/systemd/system/systemd-volatile-root.service
-rw-r--r-- 1 root root 1.4K Mar 11  2022 /usr/lib/systemd/system/system-update-cleanup.service
-rw-r--r-- 1 root root  309 Jul  5 04:37 /usr/lib/systemd/system/thermald.service
-rw-r--r-- 1 root root  830 Jun 26 17:49 /usr/lib/systemd/system/ua-reboot-cmds.service
-rw-r--r-- 1 root root  640 Jun 26 17:49 /usr/lib/systemd/system/ua-timer.service
-rw-r--r-- 1 root root  434 Oct  6  2022 /usr/lib/systemd/system/ubuntu-advantage-desktop-daemon.service
-rw-r--r-- 1 root root 1.4K Jun 26 17:49 /usr/lib/systemd/system/ubuntu-advantage.service
lrwxrwxrwx 1 root root   21 Mar 20 07:32 /usr/lib/systemd/system/udev.service -> systemd-udevd.service
-rw-r--r-- 1 root root  207 Apr  7  2022 /usr/lib/systemd/system/udisks2.service
-rw-r--r-- 1 root root  333 Jan  5  2022 /usr/lib/systemd/system/ufw.service
-rw-r--r-- 1 root root  377 Feb 19  2021 /usr/lib/systemd/system/unattended-upgrades.service
-rw-r--r-- 1 root root  240 Feb 27  2023 /usr/lib/systemd/system/update-notifier-download.service
-rw-r--r-- 1 root root  251 Feb 27  2023 /usr/lib/systemd/system/update-notifier-motd.service
-rw-r--r-- 1 root root  994 Mar  9  2022 /usr/lib/systemd/system/upower.service
-rw-r--r-- 1 root root  273 Mar 25  2022 /usr/lib/systemd/system/usb_modeswitch@.service
-rw-r--r-- 1 root root  171 Mar 25  2022 /usr/lib/systemd/system/usbmuxd.service
-rw-r--r-- 1 root root  696 Mar 20 07:32 /usr/lib/systemd/system/user-runtime-dir@.service
-rw-r--r-- 1 root root  756 Mar 20 07:32 /usr/lib/systemd/system/user@.service
-rw-r--r-- 1 root root  538 Feb 20  2022 /usr/lib/systemd/system/uuidd.service
-rw-r--r-- 1 root root  692 Jun 19 18:54 /usr/lib/systemd/system/virtlockd.service
-rw-r--r-- 1 root root  825 Jun 19 18:54 /usr/lib/systemd/system/virtlogd.service
-rw-r--r-- 1 root root  167 Apr  6  2022 /usr/lib/systemd/system/wacom-inputattach@.service
-rw-r--r-- 1 root root  217 Feb 22  2022 /usr/lib/systemd/system/whoopsie.service
-rw-r--r-- 1 root root  484 Jun  3  2022 /usr/lib/systemd/system/wpa_supplicant-nl80211@.service
-rw-r--r-- 1 root root  342 Jun  3  2022 /usr/lib/systemd/system/wpa_supplicant.service
-rw-r--r-- 1 root root  446 Jun  3  2022 /usr/lib/systemd/system/wpa_supplicant@.service
-rw-r--r-- 1 root root  478 Jun  3  2022 /usr/lib/systemd/system/wpa_supplicant-wired@.service
lrwxrwxrwx 1 root root    9 Mar 20 07:32 /usr/lib/systemd/system/x11-common.service -> /dev/null
-rw-r--r-- 1 root root  376 Feb  8  2022 /usr/lib/systemd/system/xfs_scrub_all.service
-rw-r--r-- 1 root root  272 Feb  8  2022 /usr/lib/systemd/system/xfs_scrub_fail@.service
-rw-r--r-- 1 root root  541 Feb  8  2022 /usr/lib/systemd/system/xfs_scrub@.service
-rw-r--r-- 1 root root  582 Jan 18  2023 /usr/lib/systemd/system/zfs-import-cache.service
-rw-r--r-- 1 root root  552 Jan 18  2023 /usr/lib/systemd/system/zfs-import-scan.service
lrwxrwxrwx 1 root root    9 Jan 18  2023 /usr/lib/systemd/system/zfs-import.service -> /dev/null
-rw-r--r-- 1 root root  356 Jan 18  2023 /usr/lib/systemd/system/zfs-load-module.service
-rw-r--r-- 1 root root  378 Jan 18  2023 /usr/lib/systemd/system/zfs-mount.service
-rw-r--r-- 1 root root  406 Jan 18  2023 /usr/lib/systemd/system/zfs-scrub@.service
-rw-r--r-- 1 root root  433 Jan 18  2023 /usr/lib/systemd/system/zfs-share.service
-rw-r--r-- 1 root root  291 Jan 18  2023 /usr/lib/systemd/system/zfs-volume-wait.service
-rw-r--r-- 1 root root  212 Jan 18  2023 /usr/lib/systemd/system/zfs-zed.service

```
The service files are located in /usr/lib/systemd/system/... The links to those active service files are located in /etc/systemd/system/ symlinked to the service file. If you edit a service file, it creates a directory/file as /etc/systemd/system/<service_name>.service.d/override.conf file, then overrides the file in /usr/lib/systemd/system/. Aliases are symlinks created in /etcsystemd/service pointing to the alised service files in /usr/lib/systemd/system/...  

If you enable a service, it creates a symlink from /etc/systemd/system/ to /usr/lib/system. If you mask it, it sends it to /dev/null.

But if you just put it anywhere, and there is a duplicate serice/unit name, then there are two factors that affect that, which you need to know to debug problems that may come up, the search paths, and order of precedence:
```

Search Paths:
   System Unit Search Path
       /etc/systemd/system.control/*
       /run/systemd/system.control/*
       /run/systemd/transient/*
       /run/systemd/generator.early/*
       /etc/systemd/system/*
       /etc/systemd/system.attached/*
       /run/systemd/system/*
       /run/systemd/system.attached/*
       /run/systemd/generator/*
       ...
       /lib/systemd/system/*
       /run/systemd/generator.late/*

   User Unit Search Path
       ~/.config/systemd/user.control/*
       $XDG_RUNTIME_DIR/systemd/user.control/*
       $XDG_RUNTIME_DIR/systemd/transient/*
       $XDG_RUNTIME_DIR/systemd/generator.early/*
       ~/.config/systemd/user/*
       $XDG_CONFIG_DIRS/systemd/user/*
       /etc/systemd/user/*
       $XDG_RUNTIME_DIR/systemd/user/*
       /run/systemd/user/*
       $XDG_RUNTIME_DIR/systemd/generator/*
       $XDG_DATA_HOME/systemd/user/*
       $XDG_DATA_DIRS/systemd/user/*
       ...
       /usr/lib/systemd/user/*
       $XDG_RUNTIME_DIR/systemd/generator.late/*

Order of Precedence:
       In addition to /etc/systemd/system, the drop-in ".d/" directories for system services can
       be placed in /lib/systemd/system or /run/systemd/system directories. Drop-in files in
       /etc/ take precedence over those in /run/ which in turn take precedence over those in
       /lib/. Drop-in files under any of these directories take precedence over unit files
       wherever located. Multiple drop-in files with different names are applied in lexicographic
       order, regardless of which of the directories they reside in.

```
Just thought I would add some things to think about. Like I said, you can do what you want, but if you have problems with that, then here are some things to look at.

---

