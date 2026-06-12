---
title: "Boot problem"
date: 2017-06-28
forum: Ubuntu Development Version
---

### Post by P-I H on 2017-06-28
I have installed today's ISO and the ISO from 26/7 and the installations will not boot correctly.
However when I hit the Ctrl key repeatedly after the expected boot time, I get the "splash" screen, the system boots OK and I get the login screen.
Login with "Ubuntu" is OK, but if I change to "Ubuntu on Wayland" I'm returned to the login screen.
In case I wait longer before I hit the Crtl key, systemd-analyze reports a longer boot time.
This is the boot time after I wait about 40 sec.
```
p-i@pi-GA-990FXA-UD3:~$ systemd-analyze
Startup finished in 1min 4.425s (kernel) + 10.587s (userspace) = 1min 15.012s
p-i@pi-GA-990FXA-UD3:~$ 

```

This might depend on the hardware.
```
p-i@pi-GA-990FXA-UD3:~$ inxi -F
System:    Host: pi-GA-990FXA-UD3 Kernel: 4.10.0-22-generic x86_64 (64 bit)
           Desktop: Gnome 3.24.2
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x
           BIOS: Award v: F5 date: 10/13/2011
CPU:       Octa core AMD FX-8120 Eight-Core (-MCP-) cache: 16384 KB 
           clock speeds: max: 4000 MHz 1: 1900 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1900 MHz 5: 1900 MHz 6: 1400 MHz 7: 2800 MHz 8: 1400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts PRO [Radeon HD 6850]
           Display Server: X.Org 1.19.3 drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD BARTS (DRM 2.49.0 / 4.10.0-22-generic, LLVM 4.0.1)
           GLX Version: 3.0 Mesa 17.1.2
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Barts HDMI Audio [Radeon HD 6790/6850/6870 / 7720 OEM]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-22-generic
Network:   Card-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k
           IF: wlp3s0 state: down mac: 36:83:1f:11:7f:6f
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full
           
Drives:    HDD Total Size: 880.2GB (0.8% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
           ID-2: /dev/sdb model: KINGSTON_SV300S3 size: 120.0GB
           ID-3: /dev/sdc model: WDC_WD6400AAKS size: 640.1GB
Partition: ID-1: / size: 110G used: 6.2G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 22.4C mobo: N/A gpu: 39.5
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 252 Uptime: 28 min Memory: 1547.1/7963.2MB
           Client: Shell (bash) inxi: 2.3.11 
p-i@pi-GA-990FXA-UD3:~$
``` 

The behavior is the same with proposed enabled.

---

### Post by PJs Ronin on 2017-06-28
Does ```
systemd-analyze blame
``` offer any insite?

---

### Post by P-I H on 2017-06-28
No.
Waited longer before I hit Ctrl.
```
p-i@pi-GA-990FXA-UD3:~$ systemd-analyze
Startup finished in 9min 15.208s (kernel) + 8.837s (userspace) = 9min 24.046s
p-i@pi-GA-990FXA-UD3:~$ systemd-analyze blame
          7.967s NetworkManager-wait-online.service
          1.598s fwupd.service
           710ms dev-sda1.device
           408ms systemd-resolved.service
           262ms apparmor.service
           262ms lvm2-monitor.service
           255ms systemd-timesyncd.service
           200ms ModemManager.service
           189ms networking.service
           184ms accounts-daemon.service
           160ms systemd-logind.service
           156ms upower.service
           153ms grub-common.service
           130ms systemd-rfkill.service
           127ms keyboard-setup.service
           122ms systemd-udev-trigger.service
           120ms gpu-manager.service
           114ms rsyslog.service
           109ms pppd-dns.service
           105ms thermald.service
            93ms udisks2.service
            81ms systemd-journald.service
            71ms swapfile.swap
lines 1-23
```

---

### Post by #&amp;thj^% on 2017-06-28
That output may not have shown everything: You can just hit enter or page down to show more.
```
systemd-analyze blame
          5.587s ufw.service
          5.241s udisks2.service
          3.934s nmbd.service
          3.902s dev-sda1.device
          3.101s accounts-daemon.service
          2.273s polkit.service
          1.896s ldconfig.service
          1.216s systemd-rfkill.service
          1.212s systemd-hwdb-update.service
          1.132s NetworkManager.service
          1.096s smbd.service
           887ms upower.service
           801ms systemd-udevd.service
           743ms systemd-tmpfiles-setup.service
           712ms systemd-sysusers.service
           680ms systemd-resolved.service
           609ms geoclue.service
           563ms systemd-modules-load.service
           526ms avahi-daemon.service
           428ms systemd-udev-trigger.service
           424ms dev-disk-by\x2duuid-c58b038b\x2d7a51\x2d48e9\x2d8008\x2d1f53fef
           326ms systemd-journal-catalog-update.service
           309ms systemd-tmpfiles-setup-dev.service
           308ms lightdm.service
           284ms org.cups.cupsd.service
           260ms wpa_supplicant.service
           256ms systemd-sysctl.service
           234ms sys-kernel-debug.mount
           233ms dev-mqueue.mount
           232ms kmod-static-nodes.service
           231ms dev-hugepages.mount
           231ms systemd-remount-fs.service
           193ms systemd-user-sessions.service
           192ms systemd-networkd.service
           192ms systemd-journal-flush.service
           190ms systemd-hostnamed.service
           185ms systemd-random-seed.service
           166ms systemd-logind.service
           164ms alsa-restore.service
           137ms bluetooth.service
            77ms user@1001.service
            68ms systemd-backlight@backlight:acpi_video0.service
            62ms systemd-binfmt.service
            61ms systemd-journald.service
            52ms systemd-update-utmp.service
            45ms systemd-tmpfiles-clean.service
            35ms systemd-update-done.service
            23ms rtkit-daemon.service
             2ms sys-kernel-config.mount
             2ms tmp.mount
             2ms proc-sys-fs-binfmt_misc.mount
             1ms sys-fs-fuse-connections.mount
lines 30-52/52 (END)

```
But I have no delays just an example of what is shown. :)

---

### Post by P-I H on 2017-06-28
A more complete "system-analyze blame"
```
p-i@pi-GA-990FXA-UD3:~$ systemd-analyze
Startup finished in 15min 1.467s (kernel) + 8.573s (userspace) = 15min 10.041s
p-i@pi-GA-990FXA-UD3:~$ systemd-analyze blame
          7.737s NetworkManager-wait-online.service
          1.592s fwupd.service
           580ms dev-sda1.device
           426ms lvm2-monitor.service
           415ms systemd-resolved.service
           361ms systemd-tmpfiles-clean.service
           142ms keyboard-setup.service
           135ms upower.service
           131ms systemd-udev-trigger.service
           122ms systemd-timesyncd.service
           109ms setvtrgb.service
            92ms apparmor.service
            87ms ModemManager.service
            86ms udisks2.service
            84ms systemd-journald.service
            82ms plymouth-quit-wait.service
            80ms swapfile.swap
            78ms gpu-manager.service
            77ms systemd-rfkill.service
            76ms accounts-daemon.service
            64ms grub-common.service
            60ms systemd-tmpfiles-setup.service
            58ms lightdm.service
            56ms packagekit.service
            55ms networking.service
            53ms irqbalance.service
            53ms apport.service
            49ms systemd-logind.service
            47ms rtkit-daemon.service
            44ms NetworkManager.service
            44ms rsyslog.service
            40ms user@1000.service
            34ms avahi-daemon.service
            33ms systemd-tmpfiles-setup-dev.service
            29ms lm-sensors.service
            29ms systemd-modules-load.service
            29ms speech-dispatcher.service
            27ms polkit.service
            26ms geoclue.service
            22ms systemd-udevd.service
            20ms thermald.service
            19ms plymouth-start.service
            18ms dns-clean.service
            18ms hddtemp.service
            16ms pppd-dns.service
            15ms ubiquity.service
            15ms alsa-restore.service
            15ms plymouth-read-write.service
            13ms sys-kernel-debug.mount
            11ms colord.service
            11ms ureadahead-stop.service
            10ms snapd.autoimport.service
            10ms ufw.service
             9ms systemd-journal-flush.service
             8ms dev-mqueue.mount
             8ms systemd-update-utmp.service
             8ms dev-hugepages.mount
             7ms console-setup.service
             6ms systemd-update-utmp-runlevel.service
             6ms systemd-remount-fs.service
             6ms systemd-sysctl.service
             5ms kmod-static-nodes.service
             4ms systemd-user-sessions.service
             4ms wpa_supplicant.service
             4ms systemd-random-seed.service
             3ms resolvconf.service
             3ms snapd.socket
             2ms sys-fs-fuse-connections.mount
lines 46-68/68 (END)

```

Looked at Syslog but I found no interesting information after doing this
- restarted at time 19:03 and the grub menu was shown
- hit the "down arrow" to make a pause
- selected Ubuntu in the grub menu at time 19:18
- started to hit the Ctrl key at time 19:33
- made login at time 19:37
Noting is shown in syslog between 19:03 and 19:33
```
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1399]: Stopped D-Bus User Message Bus.
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1399]: Stopped Zeitgeist full-text search indexer.
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1399]: Stopped Zeitgeist activity log service.
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping Disk Manager...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopped target Graphical Interface.
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping RealtimeKit Scheduling Policy Service...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping Accounts Service...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopped target Multi-User System.
Jun 28 19:03:06 pi-GA-990FXA-UD3 ModemManager[949]: <info>  Caught signal, shutting down...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping LSB: disk temperature monitoring daemon...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping Modem Manager...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping crash report submission daemon...
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping Regular background program processing daemon...
Jun 28 19:03:06 pi-GA-990FXA-UD3 udisksd[1630]: udisks daemon version 2.1.8 exiting
Jun 28 19:03:06 pi-GA-990FXA-UD3 systemd[1]: Stopping LSB: daemon to balance interrupts for SMP systems...
Jun 28 19:03:06 pi-GA-990FXA-UD3 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="941" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jun 28 19:33:06 pi-GA-990FXA-UD3 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1008" x-info="http://www.rsyslog.com"] start
Jun 28 19:33:06 pi-GA-990FXA-UD3 rsyslogd: rsyslogd's groupid changed to 108
Jun 28 19:33:06 pi-GA-990FXA-UD3 rsyslogd: rsyslogd's userid changed to 104
Jun 28 19:33:06 pi-GA-990FXA-UD3 systemd-modules-load[397]: Inserted module 'lp'
Jun 28 19:33:06 pi-GA-990FXA-UD3 systemd-modules-load[397]: Inserted module 'ppdev'
Jun 28 19:33:06 pi-GA-990FXA-UD3 systemd-modules-load[397]: Inserted module 'parport_pc'
Jun 28 19:33:06 pi-GA-990FXA-UD3 keyboard-setup.sh[396]:  * Setting up keyboard layout...

```

---

### Post by oldfred on 2017-06-28
Gigabyte AMD boards have had issues with IOMMU.
Most have to change a BIOS/UEFI setting and then add a boot parameter as you boot to test if it works - iommu=soft
And then permanently add
 GRUB_CMDLINE_LINUX="iommu=soft" 



 Asus Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[URL="http://ubuntuforums.org/showthread.php?t=2254677"]http://ubuntuforums.org/showthread.php?t=2254677
[/URL]
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5) 

[URL="http://ubuntuforums.org/showthread.php?t=2254677"]
[/URL]

---

### Post by P-I H on 2017-06-29
Could have been that problem, but no.

The computer is a triple boot system with Artful, Windows and Artful on different disks.
Before it booted OK with Arful upgraded from Ubuntu 17.04 and also an earlier ISO.

Will try an upgraded version again.

---

### Post by P-I H on 2017-06-29
Installation of Ubuntu 17.04 went OK
Upgrade to Artful went OK with 
[B]sudo apt update
sudo apt upgrade[/B]
**sudo update-manager -d** 

Boot went OK.

I suppose I have to wait for a new ISO.

---

### Post by corradoventu on 2017-06-30
I have same problem (Ubuntu logon is ok, Ubuntu on wayland returns to login screen) on 17.10 from ISO: Ubuntu 17.10 "Artful Aardvark" - Alpha amd64 (20170626)
the problem does not occur with 2 other installations (same computer different partitions) from: Ubuntu 17.10 "Artful Aardvark" - Alpha amd64 (20170620) and Ubuntu 17.10 "Artful Aardvark" - Alpha amd64 (20170611).
all installations downloading software from main server, proposed enabled, updated today. Here is the inxi output from the failing system:```
corrado@corrado-art3:~$ cd Documents
corrado@corrado-art3:~/Documents$ ./inxi -Fxx
System:    Host: corrado-art3 Kernel: 4.11.0-9-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu2) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: Gigabyte model: H87M-D3H v: x.x UEFI: American Megatrends v: F3 date: 04/24/2013
CPU:       Dual core Intel Core i3-4130 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13567
           clock speeds: min/max: 800/3400 MHz 1: 3272 MHz 2: 2898 MHz 3: 3305 MHz 4: 1729 MHz
Graphics:  Card: Intel 4th Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0 chip-ID: 8086:041e
           Display Server: x11 (X.Org 1.19.3) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1680x1050@59.88hz
           OpenGL: renderer: Mesa DRI Intel Haswell version: 4.5 Mesa 17.1.2 (compat-v: 3.0) Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:8c20
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0 chip-ID: 8086:0c0c
           Sound: Advanced Linux Sound Architecture v: k4.11.0-9-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0 chip-ID: 10ec:8168
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: 94:de:80:7e:90:a7
Drives:    HDD Total Size: 1000.2GB (3.4% used)
           ID-1: /dev/sda model: ST1000DM003 size: 1000.2GB serial: Z1D6YBFR
Partition: ID-1: / size: 32G used: 6.0G (20%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 225 Uptime: 18 min Memory: 1001.9/7861.1MB Init: systemd v: 233 runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121 running in gnome-terminal-) inxi: 2.3.22 
corrado@corrado-art3:~/Documents$ 

```

---

### Post by VMC on 2017-06-30
If you have a swap partition, does the UUID match up with  '/etc/fstab'

---

### Post by P-I H on 2017-06-30
In the installation I select "Use the whole disk" and then the wanted disk.
It doesn't matter if I select sda or sdc.
I installed today's daily 30/6 on sdc. The result was the same. Grub is shown, I am able to select wanted system, but the boot don't finish. The DVD activity lamp is blinking, but the HDD lamp isn't. When I press Ctrl repeatedly the HDD lamp starts blinking.
/etc/fstab looks like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
UUID=4c6d3691-3115-4790-bc3e-c52a1c52818a /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
```

---

### Post by corradoventu on 2017-07-01
My SWAP UUID matches. But this can not be the problem, the SWAP file is the same logging on 'Ubuntu' or 'Ubuntu-Wayland'
I don't find an open Bug for this problem. Did you?

---

### Post by corradoventu on 2017-07-01
I have a multiboot of various artful installed on different partitions of same disk. So I tried login on Ubuntu-wayland, failed, and rebooted on a different partition so the log of the failed wayland session was not modified. From the different partition i see the following syslog:```
Jul  1 15:47:22 corrado-art3 lightdm[1083]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul  1 15:47:22 corrado-art3 lightdm[1083]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul  1 15:47:22 corrado-art3 systemd[1]: Created slice User Slice of corrado.
Jul  1 15:47:22 corrado-art3 systemd[1]: Starting User Manager for UID 1000...
Jul  1 15:47:22 corrado-art3 systemd[1]: Started Session c2 of user corrado.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Starting D-Bus User Message Bus Socket.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Reached target Timers.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Reached target Paths.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Listening on D-Bus User Message Bus Socket.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Reached target Sockets.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Reached target Basic System.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Reached target Default.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Startup finished in 30ms.
Jul  1 15:47:23 corrado-art3 systemd[1]: Started User Manager for UID 1000.
Jul  1 15:47:23 corrado-art3 systemd[1423]: Started D-Bus User Message Bus.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1139 (lightdm) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1189 (lightdm-greeter) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1193 (unity-greeter) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1195 (at-spi-bus-laun) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1201 (dbus-daemon) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1203 (at-spi2-registr) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1230 (nm-applet) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: session-c1.scope: Killing process 1233 (unity-settings-) with signal SIGTERM.
Jul  1 15:47:23 corrado-art3 systemd[1]: Stopping Session c1 of user lightdm.
Jul  1 15:47:23 corrado-art3 systemd[1]: Stopped Session c1 of user lightdm.
Jul  1 15:47:23 corrado-art3 systemd[1]: Stopping User Manager for UID 111...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Session Service...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped target Default.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping D-Bus User Message Bus...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Sound Service...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Keyboard Backend...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Power...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Virtual filesystem service...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Date & Time Backend...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopping Indicator Application Service...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Session Service.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Application Service.
Jul  1 15:47:23 corrado-art3 indicator-sound[1269]: Name lost or unable to acquire bus: com.canonical.indicator.sound
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Power.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Date & Time Backend.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Sound Service.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped D-Bus User Message Bus.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Indicator Keyboard Backend.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped Virtual filesystem service.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped target Basic System.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped target Paths.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped target Timers.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Stopped target Sockets.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Closed D-Bus User Message Bus Socket.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Reached target Shutdown.
Jul  1 15:47:23 corrado-art3 systemd[1143]: Starting Exit the Session...
Jul  1 15:47:23 corrado-art3 systemd[1143]: Received SIGRTMIN+24 from PID 1482 (kill).
Jul  1 15:47:23 corrado-art3 systemd[1]: Stopped User Manager for UID 111.
Jul  1 15:47:23 corrado-art3 systemd[1]: Removed slice User Slice of lightdm.
Jul  1 15:47:23 corrado-art3 dbus-daemon[1447]: Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service'
Jul  1 15:47:23 corrado-art3 systemd[1423]: Starting Virtual filesystem service...
Jul  1 15:47:23 corrado-art3 dbus-daemon[1447]: Successfully activated service 'org.gtk.vfs.Daemon'
Jul  1 15:47:23 corrado-art3 systemd[1423]: Started Virtual filesystem service.
Jul  1 15:47:23 corrado-art3 dbus-daemon[1447]: Activating service name='org.gnome.ScreenSaver'
Jul  1 15:47:23 corrado-art3 org.gnome.ScreenSaver[1447]: Unable to init server: Could not connect: Connection refused
Jul  1 15:47:23 corrado-art3 gnome-screensav[1577]: Unable to initialize GTK+
Jul  1 15:47:23 corrado-art3 dbus-daemon[1447]: Activated service 'org.gnome.ScreenSaver' failed: Process org.gnome.ScreenSaver exited with status 1
Jul  1 15:47:23 corrado-art3 gnome-session[1434]: gnome-session-binary[1434]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
Jul  1 15:47:23 corrado-art3 gnome-session-binary[1434]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
Jul  1 15:47:24 corrado-art3 gnome-keyring-ssh.desktop[1579]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jul  1 15:47:24 corrado-art3 gnome-keyring-secrets.desktop[1581]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jul  1 15:47:24 corrado-art3 gnome-keyring-pkcs11.desktop[1582]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Jul  1 15:47:24 corrado-art3 gnome-shell[1587]: Failed to spawn Xwayland: Failed to execute child process “/usr/bin/Xwayland” (No such file or directory)
Jul  1 15:47:24 corrado-art3 kernel: [  473.425998] do_trap: 10 callbacks suppressed
Jul  1 15:47:24 corrado-art3 kernel: [  473.426000] traps: gnome-shell[1587] trap int3 ip:7f1e01a48ff1 sp:7ffe45a8c9e0 error:0 in libglib-2.0.so.0.5303.0[7f1e019f9000+112000]
Jul  1 15:47:24 corrado-art3 gnome-session[1434]: gnome-session-binary[1434]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Jul  1 15:47:24 corrado-art3 gnome-session-binary[1434]: WARNING: Application 'org.gnome.Shell.desktop' killed by signal 5
Jul  1 15:47:24 corrado-art3 gnome-session-binary[1434]: Unrecoverable failure in required component org.gnome.Shell.desktop
Jul  1 15:47:25 corrado-art3 systemd[1]: Stopping User Manager for UID 1000...
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopping D-Bus User Message Bus...
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped target Default.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopping Virtual filesystem service...
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped D-Bus User Message Bus.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped Virtual filesystem service.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped target Basic System.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped target Sockets.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Closed D-Bus User Message Bus Socket.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped target Paths.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Reached target Shutdown.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Starting Exit the Session...
Jul  1 15:47:25 corrado-art3 systemd[1423]: Stopped target Timers.
Jul  1 15:47:25 corrado-art3 systemd[1423]: Received SIGRTMIN+24 from PID 1601 (kill).
Jul  1 15:47:25 corrado-art3 systemd[1]: Stopped User Manager for UID 1000.
Jul  1 15:47:25 corrado-art3 systemd[1]: Removed slice User Slice of corrado.
Jul  1 15:47:25 corrado-art3 lightdm[1083]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jul  1 15:47:25 corrado-art3 systemd[1]: Created slice User Slice of lightdm.
Jul  1 15:47:25 corrado-art3 systemd[1]: Starting User Manager for UID 111...
Jul  1 15:47:25 corrado-art3 systemd[1]: Started Session c3 of user lightdm.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Reached target Timers.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Starting D-Bus User Message Bus Socket.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Reached target Paths.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Listening on D-Bus User Message Bus Socket.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Reached target Sockets.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Reached target Basic System.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Reached target Default.
Jul  1 15:47:25 corrado-art3 systemd[1612]: Startup finished in 14ms.
Jul  1 15:47:25 corrado-art3 systemd[1]: Started User Manager for UID 111.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started D-Bus User Message Bus.
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service'
Jul  1 15:47:26 corrado-art3 org.a11y.atspi.Registry[1632]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jul  1 15:47:26 corrado-art3 systemd[1612]: Starting Virtual filesystem service...
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Successfully activated service 'org.gtk.vfs.Daemon'
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Virtual filesystem service.
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Activating service name='ca.desrt.dconf'
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Successfully activated service 'ca.desrt.dconf'
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Application Service.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Power.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Date & Time Backend.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Keyboard Backend.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Session Service.
Jul  1 15:47:26 corrado-art3 systemd[1612]: Started Indicator Sound Service.
Jul  1 15:47:26 corrado-art3 indicator-keyboard-service[1666]: Unable to init server: Could not connect: Connection refused
Jul  1 15:47:26 corrado-art3 indicator-keybo[1666]: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jul  1 15:47:26 corrado-art3 indicator-sound[1676]: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files
Jul  1 15:47:26 corrado-art3 dbus[932]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service'
Jul  1 15:47:26 corrado-art3 systemd[1]: Starting Time & Date Service...
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Activating service name='com.canonical.libertine.Service'
Jul  1 15:47:26 corrado-art3 dbus[932]: [system] Successfully activated service 'org.freedesktop.timedate1'
Jul  1 15:47:26 corrado-art3 systemd[1]: Started Time & Date Service.
Jul  1 15:47:26 corrado-art3 dbus-daemon[1630]: Successfully activated service 'com.canonical.libertine.Service'
Jul  1 15:47:26 corrado-art3 /usr/lib/snapd/snapd[1003]: daemon.go:176: DEBUG: uid=111;@ GET /v2/snaps/ubuntu-calendar-app 56.576µs 404
Jul  1 15:47:26 corrado-art3 rtkit-daemon[912]: Supervising 0 threads of 0 processes of 1 users.
Jul  1 15:47:26 corrado-art3 rtkit-daemon[912]: message repeated 9 times: [ Supervising 0 threads of 0 processes of 1 users.]
Jul  1 15:47:26 corrado-art3 dbus[932]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Jul  1 15:47:26 corrado-art3 rtkit-daemon[912]: Successfully made thread 1743 of process 1743 (n/a) owned by '111' high priority at nice level -11.
Jul  1 15:47:26 corrado-art3 rtkit-daemon[912]: Supervising 1 threads of 1 processes of 1 users.
Jul  1 15:47:26 corrado-art3 pulseaudio[1743]: [pulseaudio] pid.c: Daemon already running.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped target Timers.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Authorization Manager...
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Save/Restore Sound Card State...
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped target Printer.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Session c3 of user lightdm.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped target Sound Card.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Message of the Day.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Timer to automatically refresh installed snaps.
Jul  1 15:47:46 corrado-art3 systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Manage, Install and Generate Color Profiles...
Jul  1 15:47:46 corrado-art3 dbus[932]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkit.service'
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Time & Date Service...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Power...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Application Service...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Virtual filesystem service...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Sound Service...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped target Default.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping D-Bus User Message Bus...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Session Service...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Keyboard Backend...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopping Indicator Date & Time Backend...
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Application Service.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Power.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Date & Time Backend.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Keyboard Backend.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Session Service.
Jul  1 15:47:46 corrado-art3 systemd[1612]: Stopped Indicator Sound Service.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping User Manager for UID 111...
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Daily apt upgrade and clean activities.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Trigger anacron every hour.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Daemon for power management...
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped target Graphical Interface.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopped target Multi-User System.
Jul  1 15:47:46 corrado-art3 systemd[1]: Stopping Samba SMB Daemon...
Jul  1 15:47:46 corrado-art3 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="988" x-info="http://www.rsyslog.com"] exiting on signal 15.
```
at 15:47:24 I see:
Jul  1 15:47:24 corrado-art3 gnome-shell[1587]: Failed to spawn Xwayland: Failed to execute child process “/usr/bin/Xwayland” (No such file or directory)

---

### Post by corradoventu on 2017-07-01
I checked, Xwayland exists on my Artful installed from the old daily ISO dated 20170611: 
```

corrado@corrado-art2:/usr/bin$ ls Xwayland -l
-rwxr-xr-x 1 root root 2295192 mag 10 12:03 Xwayland
corrado@corrado-art2:/usr/bin$ 

corrado@corrado-art2:/usr/bin$ inxi -SP
System:    Host: corrado-art2 Kernel: 4.11.0-8-generic x86_64 (64 bit)
           Desktop: Gnome 3.24.2
           Distro: Ubuntu Artful Aardvark (development branch)
Partition: ID-1: / size: 32G used: 7.8G (27%) fs: ext4 dev: /dev/sda4
           ID-2: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
corrado@corrado-art2:/usr/bin$ 

```
but does not exist on my Arfful installed from daily ISO dated 20170626
```
corrado@corrado-art2:/media/corrado/p8-aa-0626/usr/bin$ ls Xw*
ls: cannot access 'Xw*': No such file or directory
corrado@corrado-art2:/media/corrado/p8-aa-0626/usr/bin$ 

```

---

### Post by corradoventu on 2017-07-01
I opened a bug for this problem: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1701822](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1701822)

---

### Post by corradoventu on 2017-07-02
Fix committed. Xwayland has been installed with the last upgrade (from proposed?).
Start-Date: 2017-07-02  07:24:12
Commandline: aptdaemon role='role-commit-packages' sender=':1.1425'
Install: xwayland:amd64 (2:1.19.3-1ubuntu2, automatic)

---

