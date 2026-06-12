---
title: "Interesting systemd-analyze"
date: 2015-06-15
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-06-15
Interesting systemd-analyze after dist-upgrading just a few minutes ago in Gnome Wily.

```
systemd-analyze
Bootup is not yet finished. Please try again later.

```

---

### Post by sammiev on 2015-06-15
Fully update 15.10 gnome and not seeing that but I'm running it in a VM.

---

### Post by Chanath on 2015-06-15
It took a long time to boot today. Systemd-analyze is back, though.
> czanat@B460:~$ systemd-analyze
Startup finished in 14.977s (kernel) + 3min 5.287s (userspace) = 3min 20.265s

I'm going to watch this for while. Does it happen to you guys in any Ubuntu flavour?

---

### Post by fjgaude on 2015-06-16
I had issues with systemd earlier but all seem normal now:

frank@flash:~$ inxi -b
System:    Host: flash Kernel: 3.19.0-20-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASRock model: Z87E-ITX
           Bios: American Megatrends v: P2.50 date: 07/11/2014
CPU:       Quad core Intel Core i5-4670K (-MCP-) speed/max: 2400/4000 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.17.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 10.5.2 
Network:   Card-1: Intel Ethernet Connection I217-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: wl
Drives:    HDD Total Size: 884.2GB (28.5% used)
Info:      Processes: 214 Uptime: 2 min Memory: 573.2/15716.2MB
             Client: Shell (bash) inxi: 2.2.16 
frank@flash:~$ sudo systemd-analyze
Startup finished in **1.215s** (kernel) + **8.523s** (userspace) =** 9.739s**

---

### Post by VMC on 2015-06-16
Using Xubuntu Wiley current it works fine. Have you tried '**systemd-analyze blame**' to see if out put occurs?

---

### Post by Chanath on 2015-06-17
> **VMC said:**
> Using Xubuntu Wiley current it works fine. Have you tried '**systemd-analyze blame**' to see if out put occurs?

Today's result.```
systemd-analyze
Startup finished in 16.776s (kernel) + 3min 3.174s (userspace) = 3min 19.950s

```

Userspace is taking too long.```
[ systemd-analyze-blame
systemd-analyze-blame: command not found
```

Strange. I'd wait with some more dist-upgrades. Only waiting 3 minutes is too long.
This happens with Gnome, Kubuntu and Xubuntu Wily. All are taking more than 3 minutes to bring in userspace.

Won't install systemd-analyze-blame manually. Let dist-upgrade do it, in time.

---

### Post by dino99 on 2015-06-17
removed the typo

>  systemd-analyze blame

---

### Post by fjgaude on 2015-06-17
```
frank@flash:~$ sudo systemd-analyze
Startup finished in 1.004s (kernel) + 8.145s (userspace) = 9.150s
frank@flash:~$ sudo systemd-analyze blame
          7.191s NetworkManager-wait-online.service
           263ms vboxdrv.service
           240ms dev-disk-by\x2duuid-2ae7c6fb\x2da8cf\x2d4ad4\x2d8375\x2d61ab17f
           237ms gpu-manager.service
           148ms NetworkManager.service
            78ms ModemManager.service
            77ms rtkit-daemon.service
            61ms systemd-fsck-root.service
            56ms networking.service
            51ms binfmt-support.service
            49ms systemd-timesyncd.service
            48ms systemd-fsck@dev-disk-by\x2dlabel-BAfrank@flash:~$ sudo systemd-analyze
```

---

