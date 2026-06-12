---
title: "Boot time on Xubuntu 17.10.1"
date: 2018-01-14
forum: The Cafe
---

### Post by litlesam on 2018-01-14
Downloaded the latest Xubuntu ISO yesterday adding all my bells and whistles, it seem to boot a little faster than Xubuntu 16.04.3

Decided to run a few test and was surprised with the results.

```
~$ systemd-analyze
Startup finished in 2.595s (kernel) + 5.436s (userspace) = 8.032s
```

```
:~$ systemd-analyze blame
          3.257s NetworkManager-wait-online.service
           941ms dev-sda6.device
           679ms apparmor.service
           667ms plymouth-start.service
           599ms plymouth-read-write.service
           269ms udisks2.service
           265ms ModemManager.service
           219ms ufw.service
           200ms systemd-resolved.service
           185ms NetworkManager.service
           176ms upower.service
           161ms snapd.service
           143ms lightdm.service
           139ms plymouth-quit-wait.service
           136ms systemd-rfkill.service
           134ms accounts-daemon.service
           132ms systemd-timesyncd.service
           112ms keyboard-setup.service
           102ms gpu-manager.service

```

Not too bad for a 7 year old laptop.

---

