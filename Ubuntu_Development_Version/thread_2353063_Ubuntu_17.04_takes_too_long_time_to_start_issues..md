---
title: "Ubuntu 17.04 takes too long time to start issues."
date: 2017-02-18
forum: Ubuntu Development Version
---

### Post by hoboy on 2017-02-18
Hi
I have upgraded from 16.10 to 17.04.
Now it takes long time to launch ubuntu.
Any suggestion ?
Thanks

---

### Post by oldos2er on 2017-02-18
Moved to *Ubuntu Development Version*

---

### Post by cariboo on 2017-02-18
What do you consider a long time? I can see by running:

```
systemd-analyze
```

my boot time has doubled to a little over 13 seconds, whereas it's normally in the 5 second range.

---

### Post by hoboy on 2017-02-18
systemd-analyze
Startup finished in 8.942s (kernel) + 1min 49.311s (userspace) = 1min 58.253s

---

### Post by cecilpierce on 2017-02-18
Wish mine was that fast:
Startup finished in 9.882s (kernel) + 6min 30.059s (userspace) = 6min 39.942s

---

### Post by ventrical on 2017-02-19
I have a lot of installs of 17.04 that will phone home and download a bunch of stuff and the boot process will not finish until download is done. his This from startup. It is most intrusive if you have unity8 preview installed.systemd-analyze

```

ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ htop
ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze
Startup finished in 8.698s (firmware) + 4.041s (loader) + 1.384s (kernel) + 8min 10.116s (userspace) = 8min 24.241s
ventrical@ventrical-MS-7850:~$ 


```

Look at userspace. (8min 10.116s) All that time it was downloading some update - perhaps a snapd. Torvalds would have a fit if he seen this  and how it affects userspace. This on SSD highend PC.

> **cecilpierce said:**
> Wish mine was that fast:
Startup finished in 9.882s (kernel) + 6min 30.059s (userspace) = 6min 39.942s

Do you have unity8 preview installed ?

---

### Post by cecilpierce on 2017-02-19
Yes I have unity8 installed.

---

### Post by ventrical on 2017-02-19
> **cecilpierce said:**
> Yes I have unity8 installed.



[s]I am assuming that containers  and snaps are being upgraded on each reboot and that the boot will not complete until those items are updated .. even if you log into unity7.[/s]

Update/upgrade <systemd> seems to have resolved userspace issue .For now I have to declare a wrong assumption about snaps and unity8.

Regards..

Latest update of systemd and other components seems to bring some resolution to this one particular install.

```


ventrical@ventrical-MS-7850:~$ systemd-analyze
Startup finished in 8.185s (firmware) + 4.020s (loader) + 1.332s (kernel) + 13.704s (userspace) = 27.242s
ventrical@ventrical-MS-7850:~$ 





```

> **cariboo said:**
> What do you consider a long time? I can see by running:

```
systemd-analyze
```

my boot time has doubled to a little over 13 seconds, whereas it's normally in the 5 second range.

Just curious if you have unity8 installed?

Regards..

---

### Post by cariboo on 2017-02-19
> **ventrical said:**
> Just curious if you have unity8 installed?

Regards..

Yes I do, although I only loads to the login prompt again, when trying to start it

---

### Post by cariboo on 2017-02-19
@hoboy, Have you run:

```
systemd=analyze blame
```

to see which services are taking a long time to start?

---

### Post by ventrical on 2017-02-24
I thought I had my prob fixed but after 48 hours I booted up and working/upgraded install of unity zesty and got this:

```

Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze blame
    4min 42.027s snapd.refresh.service
    3min 18.049s apt-daily.service
          8.149s NetworkManager-wait-online.service
          2.699s ModemManager.service
          2.693s accounts-daemon.service
          2.184s dev-sda2.device
          1.702s fwupd.service
          1.585s networking.service
          1.457s upower.service
          1.356s systemd-update-utmp.service
          1.216s apport.service
          1.216s click-system-hooks.service
          1.215s irqbalance.service
          1.211s repowerd.service
          1.189s grub-common.service
          1.185s systemd-logind.service
          1.181s alsa-restore.service
          1.173s speech-dispatcher.service
           895ms systemd-resolved.service
           870ms systemd-udev-trigger.service
           843ms keyboard-setup.service
           649ms user@1000.service
           582ms systemd-random-seed.service
           558ms lxc-net.service
           557ms systemd-udevd.service
           480ms openvpn.service
           395ms thermald.service
           392ms sysstat.service
           382ms lm-sensors.service
           378ms NetworkManager.service
           374ms gpu-manager.service
           374ms avahi-daemon.service
           295ms snap-vlc-1.mount
           294ms snap-core-1240.mount
           288ms dev-loop1.device
           284ms lightdm.service
           284ms plymouth-quit-wait.service
           284ms systemd-journald.service
           281ms dev-loop3.device
           277ms systemd-modules-load.service
           275ms apparmor.service
           274ms systemd-tmpfiles-setup.service
           264ms systemd-tmpfiles-setup-dev.service
           238ms snap-vlc-4.mount
           236ms systemd-timesyncd.service
           188ms hddtemp.service
           106ms snap.canonical-livepatch.canonical-livepatchd.service
            81ms lxc.service
            60ms rsyslog.service
            45ms pppd-dns.service
            39ms udisks2.service
            38ms colord.service
            33ms polkit.service
            33ms plymouth-start.service
            33ms systemd-fsck@dev-disk-by\x2duuid-9CCA\x2d1932.service
            32ms snap-canonical\x2dlivepatch-21.mount
            30ms snap-core-1337.mount
            25ms packagekit.service
            25ms snapd.autoimport.service
            24ms dev-mqueue.mount
            22ms systemd-backlight@backlight:acpi_video0.service
            18ms kmod-static-nodes.service
            18ms plymouth-read-write.service
            17ms snap-core-1222.mount
            16ms ufw.service
            16ms dev-sda3.swap
            13ms console-setup.service
            13ms snap-canonical\x2dlivepatch-17.mount
            12ms systemd-journal-flush.service
            11ms rtkit-daemon.service
            11ms sys-kernel-debug.mount
            10ms setvtrgb.service
            10ms systemd-update-utmp-runlevel.service
            10ms systemd-remount-fs.service
             8ms systemd-user-sessions.service
             8ms dev-hugepages.mount
             6ms ureadahead-stop.service
             6ms boot-efi.mount
             5ms dns-clean.service
             5ms dev-loop0.device
             4ms systemd-sysctl.service
             3ms sys-fs-fuse-connections.mount
             3ms resolvconf.service
             1ms snapd.socket
           889us dev-loop7.device
           848us dev-loop6.device
           816us dev-loop4.device
           692us dev-loop5.device

ventrical@ventrical-MS-7850:~$ 

```

```

ventrical@ventrical-MS-7850:~$ systemd-analyze
Startup finished in 8.711s (firmware) + 4.020s (loader) + 1.356s (kernel) + 4min 57.150s (userspace) = 5min 11.239s
ventrical@ventrical-MS-7850:~$ 

```

You can run apps and everything looks normal until you try to apt-get update/dist-upgrade. You have to wait for snapd-refresh-service and apt-daily-service to finish which can be anywhere from 8 to 14 minutes. This had been occurring through the yakkety cycle also. At first I thought it was a remote backdoor testing program/spyware trying to gather test information. I thought snapd had to have permission to update. Is this a security bug?

Regards..

This was supposed to be fixed in ver 2.11

[URL="https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1667882"]https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1667882

[http://askubuntu.com/questions/801077/disable-snapd-refresh-service-on-16-04-to-speed-up-boot-no-snap-packages-in-use](http://askubuntu.com/questions/801077/disable-snapd-refresh-service-on-16-04-to-speed-up-boot-no-snap-packages-in-use)
[/URL]

I thought I had my prob fixed but after 48 hours I booted up and working/upgraded install of unity zesty and got this:

```

Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7850:~$ systemd-analyze blame
    4min 42.027s snapd.refresh.service
    3min 18.049s apt-daily.service
          8.149s NetworkManager-wait-online.service
          2.699s ModemManager.service
          2.693s accounts-daemon.service
          2.184s dev-sda2.device
          1.702s fwupd.service
          1.585s networking.service
          1.457s upower.service
          1.356s systemd-update-utmp.service
          1.216s apport.service
          1.216s click-system-hooks.service
          1.215s irqbalance.service
          1.211s repowerd.service
          1.189s grub-common.service
          1.185s systemd-logind.service
          1.181s alsa-restore.service
          1.173s speech-dispatcher.service
           895ms systemd-resolved.service
           870ms systemd-udev-trigger.service
           843ms keyboard-setup.service
           649ms user@1000.service
           582ms systemd-random-seed.service
           558ms lxc-net.service
           557ms systemd-udevd.service
           480ms openvpn.service
           395ms thermald.service
           392ms sysstat.service
           382ms lm-sensors.service
           378ms NetworkManager.service
           374ms gpu-manager.service
           374ms avahi-daemon.service
           295ms snap-vlc-1.mount
           294ms snap-core-1240.mount
           288ms dev-loop1.device
           284ms lightdm.service
           284ms plymouth-quit-wait.service
           284ms systemd-journald.service
           281ms dev-loop3.device
           277ms systemd-modules-load.service
           275ms apparmor.service
           274ms systemd-tmpfiles-setup.service
           264ms systemd-tmpfiles-setup-dev.service
           238ms snap-vlc-4.mount
           236ms systemd-timesyncd.service
           188ms hddtemp.service
           106ms snap.canonical-livepatch.canonical-livepatchd.service
            81ms lxc.service
            60ms rsyslog.service
            45ms pppd-dns.service
            39ms udisks2.service
            38ms colord.service
            33ms polkit.service
            33ms plymouth-start.service
            33ms systemd-fsck@dev-disk-by\x2duuid-9CCA\x2d1932.service
            32ms snap-canonical\x2dlivepatch-21.mount
            30ms snap-core-1337.mount
            25ms packagekit.service
            25ms snapd.autoimport.service
            24ms dev-mqueue.mount
            22ms systemd-backlight@backlight:acpi_video0.service
            18ms kmod-static-nodes.service
            18ms plymouth-read-write.service
            17ms snap-core-1222.mount
            16ms ufw.service
            16ms dev-sda3.swap
            13ms console-setup.service
            13ms snap-canonical\x2dlivepatch-17.mount
            12ms systemd-journal-flush.service
            11ms rtkit-daemon.service
            11ms sys-kernel-debug.mount
            10ms setvtrgb.service
            10ms systemd-update-utmp-runlevel.service
            10ms systemd-remount-fs.service
             8ms systemd-user-sessions.service
             8ms dev-hugepages.mount
             6ms ureadahead-stop.service
             6ms boot-efi.mount
             5ms dns-clean.service
             5ms dev-loop0.device
             4ms systemd-sysctl.service
             3ms sys-fs-fuse-connections.mount
             3ms resolvconf.service
             1ms snapd.socket
           889us dev-loop7.device
           848us dev-loop6.device
           816us dev-loop4.device
           692us dev-loop5.device

ventrical@ventrical-MS-7850:~$ 

```

```

ventrical@ventrical-MS-7850:~$ systemd-analyze
Startup finished in 8.711s (firmware) + 4.020s (loader) + 1.356s (kernel) + 4min 57.150s (userspace) = 5min 11.239s
ventrical@ventrical-MS-7850:~$ 

```

You can run apps and everything looks normal until you try to apt-get update/dist-upgrade. You have to wait for snapd-refresh-service and apt-daily-service to finish which can be anywhere from 8 to 14 minutes. This had been occurring through the yakkety cycle also. At first I thought it was a remote backdoor testing program/spyware trying to gather test information. I thought snapd had to have permission to update. Is this a security bug?

Regards..

@mod

Please remove dup post

I did this to disable:

```

systemctl disable snapd.refresh.service

```

---

### Post by jerrylamos on 2017-02-25
What slows my 17.04 boot is a number of "internal errors" on every boot., for example

/var/crash

/var/crash/_usr_lib_fwupd_fwupd.0.crash

whatever that is

Some other crashes on boot try to submit and complains some obscure thing is out of date with a name 30+ characters long and can't copy it with the mouse.  
I'm always updating so I assume the complaint about "out of date" is a dodge.

Anyway, after stumbling all over itself finally goes on.

BTW this has been happening on every boot since 1704 .iso was available.

---

### Post by pixelro on 2017-02-26
same here, fwupd crashes [https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1663548](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1663548)

---

### Post by cariboo on 2017-02-26
There is a fix in the bug report.

> Commenting out PrivateUsers=yes from /lib/systemd/system/fwupd.service fixes it for me!

---

