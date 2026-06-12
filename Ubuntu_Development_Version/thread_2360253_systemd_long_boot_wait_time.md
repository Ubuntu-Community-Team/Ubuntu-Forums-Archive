---
title: "systemd long boot wait time"
date: 2017-05-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-05-02
It's back to the long boot time for systemd on wayland.

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.518s (kernel) + 4min 15.489s (userspace) = 4min 19.008s
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2017-05-06
and...

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.640s (kernel) + 18min 39.018s (userspace) = 18min 42.658s
ventrical@ventrical-System-Product-Name:~$ 

```


so this systemd bug is capricious, on again, off again like a phantom..

---

### Post by Morbius1 on 2017-05-06
Can you find the culprit by running:
```
systemd-analyze blame
```
Or:
```
systemd-analyze critical-chain
```

---

### Post by cecilpierce on 2017-05-06
How do I get gnome to boot wayland instead of xorg ?

I always have to logout and then choose gnome-wayland and login.

I have this in /etc/gdm3/custom.conf:
# Uncoment the line below to force the login screen to use Xorg
WaylandEnable=true

---

### Post by ventrical on 2017-05-08
> **Morbius1 said:**
> Can you find the culprit by running:
```
systemd-analyze blame
```
Or:
```
systemd-analyze critical-chain
```

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze blame
    5min 36.844s apt-daily.service
         11.269s plymouth-quit-wait.service
         10.275s dev-sda5.device
          8.312s ModemManager.service
          6.906s networking.service
          5.707s hddtemp.service
          5.697s NetworkManager-wait-online.service
          5.497s NetworkManager.service
          5.222s apparmor.service
          4.251s apport.service
          4.200s thermald.service
          4.187s irqbalance.service
          3.864s systemd-logind.service
          3.310s grub-common.service
          3.087s rsyslog.service
          3.086s pppd-dns.service
          2.764s rtkit-daemon.service
          2.632s accounts-daemon.service
          2.585s fwupd.service
          2.472s gpu-manager.service
          2.371s lm-sensors.service
          1.569s keyboard-setup.service
          1.487s polkit.service
          1.139s avahi-daemon.service
          1.035s speech-dispatcher.service
           980ms swapfile.swap
           951ms systemd-timesyncd.service
           892ms wpa_supplicant.service
           864ms resolvconf.service
           707ms systemd-modules-load.service
           658ms packagekit.service
           656ms systemd-udevd.service
           639ms console-setup.service
           637ms systemd-resolved.service
           563ms sys-kernel-debug.mount
           560ms dev-mqueue.mount
           531ms dev-hugepages.mount
           495ms systemd-tmpfiles-setup-dev.service
           464ms systemd-udev-trigger.service
           369ms switcheroo-control.service
           354ms kmod-static-nodes.service
           352ms systemd-random-seed.service
           289ms udisks2.service
           274ms alsa-restore.service
           249ms setvtrgb.service
           243ms systemd-journald.service
           231ms user@120.service
           228ms colord.service
           189ms systemd-tmpfiles-setup.service
           181ms systemd-sysctl.service
           180ms systemd-update-utmp.service
           175ms ufw.service
           169ms upower.service
           168ms systemd-remount-fs.service
           136ms systemd-user-sessions.service
           113ms gdm.service
            97ms snapd.socket
            72ms user@1000.service
            69ms plymouth-start.service
            54ms geoclue.service
            51ms systemd-tmpfiles-clean.service
            47ms systemd-journal-flush.service
            40ms apt-daily-upgrade.service
            11ms plymouth-read-write.service
            10ms systemd-update-utmp-runlevel.service
             9ms snapd.autoimport.service
             7ms ureadahead-stop.service
             2ms sys-fs-fuse-connections.mount

```

yea .. apt daily-service. Must be unattended upgrade or somthing.

hmmm... just seem that lm-sensors is installed by default.

---

### Post by ventrical on 2017-05-09
So I set unattended upgrades to 'never' and it solved problem.  So it was basically hijacking my PC during boot.

```

ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.730s (kernel) + 37.715s (userspace) = 41.445s
ventrical@ventrical-System-Product-Name:~$ 


```

---

### Post by jbicha on 2017-05-09
unattended-upgrades runs like once per day, but if your computer was turned off when it was supposed to run, it will run when you first boot.

---

### Post by ventrical on 2017-05-09
> **jbicha said:**
> unattended-upgrades runs like once per day, but if your computer was turned off when it was supposed to run, it will run when you first boot.

Yes . .thanks ..as harry explained for me..

---

