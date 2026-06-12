---
title: "Installation of new kernel does not write to /var/run/reboot-required on Intel x64"
date: 2022-05-25
forum: Server Platforms
---

### Post by ameinild on 2022-05-25
I have Ubuntu Server 22.04 installed on both an Intel Atom (amd64) and a Raspberry Pi (arm64).

With the last kernel update (installed by `[FONT=courier new]unattended-upgrades[/FONT]`) the files `[FONT=courier new]/var/run/reboot-required[/FONT]` and `[FONT=courier new]/var/run/reboot-required.pkgs[/FONT]` have not been created on the Intel system (and thus the system is not flagged for reboot), but on the RasPi this works as expected.

Here are the excerpts from `[FONT=courier new]/var/log/apt/history.log[/FONT]`.

Intel Atom:

```
    Start-Date: 2022-05-24  06:52:55
    Commandline: /usr/bin/unattended-upgrade
    Install: linux-image-5.15.0-33-generic:amd64 (5.15.0-33.34, automatic), linux-headers-5.15.0-33-generic:amd64 (5.15.0-33.34, automatic), linux-modules-5.15.0-33-generic:amd64 (5.15.0-33.34, automatic), linux-headers-5.15.0-33:amd64 (5.15.0-33.34, automatic), linux-modules-extra-5.15.0-33-generic:amd64 (5.15.0-33.34, automatic)
    Upgrade: linux-headers-generic:amd64 (5.15.0.30.33, 5.15.0.33.36), linux-generic:amd64 (5.15.0.30.33, 5.15.0.33.36), linux-image-generic:amd64 (5.15.0.30.33, 5.15.0.33.36)
    End-Date: 2022-05-24  06:53:41
```

Raspberry Pi:

```
    Start-Date: 2022-05-25  06:44:33
    Commandline: /usr/bin/unattended-upgrade
    Install: linux-modules-5.15.0-1008-raspi:arm64 (5.15.0-1008.8, automatic), linux-raspi-headers-5.15.0-1008:arm64 (5.15.0-1008.8, automatic), linux-image-5.15.0-1008-raspi:arm64 (5.15.0-1008.8, automatic), linux-headers-5.15.0-1008-raspi:arm64 (5.15.0-1008.8, automatic)
    Upgrade: linux-headers-raspi:arm64 (5.15.0.1006.6, 5.15.0.1008.8), linux-raspi:arm64 (5.15.0.1006.6, 5.15.0.1008.8), linux-image-raspi:arm64 (5.15.0.1006.6, 5.15.0.1008.8)
    End-Date: 2022-05-25  06:46:44
```

Test of files `[FONT=courier new]/var/run/reboot-required[/FONT]` and `[FONT=courier new]/var/run/reboot-required.pkgs[/FONT]`.

Intel Atom:

```
    $ cat /var/run/reboot-required
    cat: /var/run/reboot-required: No such file or directory
    
    $ cat /var/run/reboot-required.pkgs
    cat: /var/run/reboot-required.pkgs: No such file or directory
```

Raspberry Pi:

```
    $ cat /var/run/reboot-required
    *** System restart required ***
    
    $ cat /var/run/reboot-required.pkgs
    linux-image-5.15.0-1008-raspi
    linux-base
```

I have the package `[FONT=courier new]update-notifier-common[/FONT]` installed on both systems (was an existing solution on Ask Ubuntu). And yes, the symlink `[FONT=courier new]/run -> /var/run[/FONT]` also exist.

Both systems have been upgraded from 20.04, and here it worked as expected on both systems. It should also be noted that for other packages (like `[FONT=courier new]libssl3[/FONT]`), I'm pretty sure the `[FONT=courier new]/var/run/reboot-required[/FONT]` was updated on both systems.

This is a little annoying for me because I use these files, both to be aware that a kernel update has been installed, and also to trigger a manual reboot at a designated time. So any suggestions on how to troubleshoot this and get the `[FONT=courier new]/var/run/reboot-required[/FONT]` files to be written will be much appreciated.

*NB: I just got confirmation from a friend (also with an Intel server), and here the files have been written as expected. So it seems it's not a package bug either.*

---

### Post by LHammonds on 2022-05-25
Well, 1st thing I would check is what kernel your OS currently has loaded:
```
uname -r
5.15.0-25-generic
```
Then look in the look in /boot to see if there is a newer kernel.
```
ls -l /boot/vm*
```
If the currently loaded kernel matches the latest one in /boot, then check if your system already rebooted:
```
uptime
```
If the system did not reboot and is running the latest kernel, do you have a live patch running?

LHammonds

---

### Post by ameinild on 2022-05-25
I'm currently running 5.15.0-30-generic, and the latest installed is 5.15.0-33-generic. And the system has not rebooted since.

However, the issue here isn't really whether or not the server *has *rebooted, or which kernel it's running. 

The exact problem is that the files [FONT=courier new]/var/run/reboot-required[/FONT] and [FONT=courier new]/var/run/reboot-required.pkgs[/FONT] remain non-existent, when they should have some content in them after a new kernel was installed.

---

